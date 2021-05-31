
# Use

##### Setting => Editor => Live Templates
##### use default context ===> edit variable => context = variableOfType("android.content.Context")

<b>
<b>
<b>
<b>
    
    
        
## ColorPicker

```java
    
private void $Name$() {

}

```
    
## ColorPicker

```java

com.mrq.library.ColorPickerDialog.ColorPicker cp = new com.mrq.library.ColorPickerDialog.ColorPicker($context$);
cp.show();
cp.enableAutoClose();
cp.setCallback(new com.mrq.library.ColorPickerDialog.ColorPickerCallback() {
    @Override
    public void onColorChosen(@androidx.annotation.ColorInt int color) {
        String colors = String.format("#%06X", (0xFFFFFF & color));
    }
});

```

## ImagePopup

```java

com.mrq.library.ImagePopup.ImagePopup popup = new com.mrq.library.ImagePopup.ImagePopup($context$);
popup.initiatePopup(getDrawable(R.drawable.ic_close));
//or
//  popup.initiatePopupWithPicasso(((String) url));
// popup.setFullScreen(true);
//    popup.setHideCloseIcon(false);
//  popup.setBackgroundColor(Color.parseColor("#000000"));
//    popup.setOnImageClickListener(new View.OnClickListener() {
//      @Override
//       public void onClick(View v) {
//
//       }
// });
popup.viewPopup();

```

## onBackPressed 2 

```java
private android.widget.Toast backToasty;
private long backPressedTime;

@Override
public void onBackPressed() {
    if (backPressedTime + 2000 > System.currentTimeMillis()) {
        backToasty.cancel();
        super.onBackPressed();
        return;
    } else {
        backToasty = android.widget.Toast.makeText($context$, "Press back again to exit.", Toast.LENGTH_SHORT);
        backToasty.show();
    }
    backPressedTime = System.currentTimeMillis();
}

```

## Toasty

```java

com.mrq.library.Toasty.Toasty.custom($context$, "$message$",com.mrq.library.Toasty.ToastyUtils.getDrawable(this, $img$) , Toasty.LENGTH_SHORT,true).show();

```

    
```java

com.mrq.library.Toasty.Toasty.error($context$, "$message$", Toasty.LENGTH_SHORT,true).show();

```
    
```java

com.mrq.library.Toasty.Toasty.info($context$, "$message$", Toasty.LENGTH_SHORT,true).show();

```
    
```java


com.mrq.library.Toasty.Toasty.success($context$, "$message$", Toasty.LENGTH_SHORT,true).show();

```
    
```java

com.mrq.library.Toasty.Toasty.warning($context$, "$message$", Toasty.LENGTH_SHORT, true).show();

```
    
## YoYo

```YoYo

com.mrq.library.YoYo.YoYo.with(com.mrq.library.YoYo.Techniques.Tada)
    .duration(1000)
    .repeat($repeat$)
    .playOn($textView$);

```


# Use

##### app => java file => click right button => new => edit file Templates


## Adapter

```Adapter

#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end

import android.annotation.SuppressLint;
import android.content.Context;
import android.content.Intent;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.TextView;
import androidx.annotation.NonNull;
import androidx.recyclerview.widget.RecyclerView;
import java.util.ArrayList;

public class ${NAME}Adapter extends RecyclerView.Adapter<${NAME}Adapter.${NAME}ViewHolder> {

    private static Context mContext;
    private ArrayList<${Model_Name}> list;
    private ${Interface_Name}Interface anInterface;

    public ${NAME}Adapter(ArrayList<${Model_Name}> list, Context mContext) {
        this.list = list;
        ${NAME}Adapter.mContext = mContext;
    }

    public ${NAME}Adapter(ArrayList<${Model_Name}> list, Context mContext, ${Interface_Name}Interface anInterface) {
        this.list = list;
        ${NAME}Adapter.mContext = mContext;
        this.anInterface = anInterface;
    }

    @NonNull
    @Override
    public ${NAME}ViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext()).inflate(R.layout.${design_Name}, parent, false);
        return new ${NAME}ViewHolder(v);
    }

    @Override
    public void onBindViewHolder(@NonNull ${NAME}ViewHolder holder, final int position) {
        final ${Model_Name} model = list.get(position);
        holder.bind(model);

    }

    @Override
    public int getItemCount() {
    //    return list.size();
         return (list != null ? list.size() : 0);
    }

    static class ${NAME}ViewHolder extends RecyclerView.ViewHolder {

        private TextView tv_title;

        private ${NAME}ViewHolder(@NonNull View itemView) {
            super(itemView);

            tv_title = itemView.findViewById(R.id.custom_tv_title);

        }

        @SuppressLint("SetTextI18n")
        private void bind(${Model_Name} model) {

        }
    }

}

```


## Adapter Filter

```AdapterFilter

#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end

import android.annotation.SuppressLint;
import android.content.Context;
import android.content.Intent;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.ImageView;
import android.widget.TextView;
import androidx.annotation.NonNull;
import androidx.recyclerview.widget.RecyclerView;
import java.util.ArrayList;
import java.util.List;

import android.widget.Filter;
import android.widget.Filterable;

public class ${NAME}Adapter extends RecyclerView.Adapter<${NAME}Adapter.${NAME}ViewHolder> implements Filterable{

    private static Context mContext;
    private ArrayList<${Model_Name}> list;
    private List<${Model_Name}> exampleListFull;
    private ${Interface_Name}Interface anInterface;

    public ${NAME}Adapter(ArrayList<${Model_Name}> list, Context mContext) {
        this.list = list;
        ${NAME}Adapter.mContext = mContext;
        exampleListFull = new ArrayList<>(list);
    }

    public ${NAME}Adapter(ArrayList<${Model_Name}> list, Context mContext, ${Interface_Name}Interface anInterface) {
        this.list = list;
        ${NAME}Adapter.mContext = mContext;
        this.anInterface = anInterface;
        exampleListFull = new ArrayList<>(list);
    }

    @NonNull
    @Override
    public ${NAME}ViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext()).inflate(R.layout.${design_Name}, parent, false);
        return new ${NAME}ViewHolder(v);
    }

    @Override
    public void onBindViewHolder(@NonNull ${NAME}ViewHolder holder, final int position) {
        final ${Model_Name} model = list.get(position);
        holder.bind(model);

    }

    @Override
    public int getItemCount() {
         return (list != null ? list.size() : 0);
    }

    static class ${NAME}ViewHolder extends RecyclerView.ViewHolder {

        private TextView tv_title;

        private ${NAME}ViewHolder(@NonNull View itemView) {
            super(itemView);

            tv_title = itemView.findViewById(R.id.custom_tv_title);

        }

        private void bind(${Model_Name} model) {

        }
    }
@Override
public Filter getFilter() {
        return exampleFilter;
        }

private Filter exampleFilter = new Filter() {
@Override
protected FilterResults performFiltering(CharSequence constraint) {
        List<${Model_Name}> filteredList = new ArrayList<>();

        if (constraint == null || constraint.length() == 0) {
        filteredList.addAll(exampleListFull);
        } else {
        String filterPattern = constraint.toString().toLowerCase().trim();

        for (${Model_Name} item : exampleListFull) {
        if (item.getName().toLowerCase().contains(filterPattern)) {
        filteredList.add(item);
        }
        }
        }

        FilterResults results = new FilterResults();
        results.values = filteredList;

        return results;
        }

@Override
protected void publishResults(CharSequence constraint, FilterResults results) {
        list.clear();
        list.addAll((List) results.values);
        notifyDataSetChanged();
        }
        };

}

```

## custom Interface

```customInterface

#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
        #parse("File Header.java")
public interface ${NAME}Interface {
        void onClick(${Model_Name} model);
        }


```








