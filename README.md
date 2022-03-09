
# Use

##### Setting => Editor => Live Templates
##### use default context ===> edit variable => context = variableOfType("android.content.Context")
##### applicable contexts  => out onCreate use (Declaration) 
##### applicable contexts  => inside onCreate use (Expression) 

<b>
<b>
<b>
<b>
    
## BaseAdapter

```java
    
BaseAdapter<$model$> adapter = new BaseAdapter<$model$>($context$, list) {
            @Override
            public RecyclerView.ViewHolder setViewHolder(android.view.ViewGroup parent) {
                final android.view.View view = android.view.LayoutInflater.from(getApplicationContext())
                        .inflate(R.layout.$layout$, parent, false);
                return new $holder$(getApplicationContext(), view);
            }

            @Override
            public void onBindData(RecyclerView.ViewHolder holders, Inbox val) {
                $holder$ holder = ($holder$) holders;
//                com.bumptech.glide.Glide.with($context$).load("")
//                        .placeholder(R.drawable.ic_launcher_background).into(holder.img);
//                holder.getText().setText(val.getTitle());
            }
        };
        rv.setAdapter(adapter);
    
    
   
```
    
## fun

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

```java

com.mrq.library.YoYo.YoYo.with(com.mrq.library.YoYo.Techniques.Tada)
    .duration(1000)
    .repeat($repeat$)
    .playOn($textView$);

```


# Use

##### app => java file => click right button => new => edit file Templates


## Adapter

```java


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

     Context mContext;
     ArrayList<${Model_Name}> list;

    public ${NAME}Adapter(ArrayList<${Model_Name}> list, Context mContext) {
        this.list = list;
        this.mContext = mContext;
    }

    @NonNull
    @Override
    public ${NAME}ViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
        View v = LayoutInflater.from(parent.getContext()).inflate(R.layout.${design_Name}, parent, false);
        return new ${NAME}ViewHolder(v);
    }

    @Override
    public void onBindViewHolder(@NonNull ${NAME}ViewHolder holder, int position) {
        ${Model_Name} model = list.get(position);
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

        @SuppressLint("SetTextI18n")
        private void bind(${Model_Name} model) {

        }
    }

}


```


## Adapter Filter

```java

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

    
## Adapter SectionTitle

```java
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
import com.mrq.library.FastScroll.SectionTitleProvider;
import java.util.ArrayList;

public class ${NAME}Adapter extends RecyclerView.Adapter<${NAME}Adapter.${NAME}ViewHolder> 
 implements SectionTitleProvider {

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
    
    private String getData(int position) {
        return list.get(position);
    }

    @Override
    public String getSectionTitle(int position) {
        return getData(position).substring(0, 1);
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

    
    
## custom Interface

```java

#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end
        #parse("File Header.java")
public interface ${NAME}Interface {
        void onClick(${Model_Name} model);
        }


```



    
    
## custom BaseAdapter

```java

#if (${PACKAGE_NAME} && ${PACKAGE_NAME} != "")package ${PACKAGE_NAME};#end

import android.content.Context;
import android.view.ViewGroup;

import androidx.recyclerview.widget.RecyclerView;

import org.jetbrains.annotations.NotNull;

import java.util.ArrayList;

public abstract class BaseAdapter<T> extends RecyclerView.Adapter<RecyclerView.ViewHolder> {

    private Context mContext;
    private ArrayList<T> list;

    public abstract RecyclerView.ViewHolder setViewHolder(ViewGroup parent);

    public abstract void onBindData(RecyclerView.ViewHolder holder, T val);

    public BaseAdapter(Context mContext, ArrayList<T> list) {
        this.mContext = mContext;
        this.list = list;
    }

    @NotNull
    @Override
    public RecyclerView.ViewHolder onCreateViewHolder(@NotNull ViewGroup parent, int viewType) {
        RecyclerView.ViewHolder holder = setViewHolder(parent);
        holder.setIsRecyclable(false);
        return holder;
    }

    @Override
    public void onBindViewHolder(@NotNull RecyclerView.ViewHolder holder, int position) {
        onBindData(holder, list.get(position));
    }

    @Override
    public int getItemCount() {
        return list.size();
    }

    public void addItems(ArrayList<T> savedCardItems) {
        list = savedCardItems;
        this.notifyDataSetChanged();
    }

    public T getItem(int position) {
        return list.get(position);
    }

}

```
    
    
 ## custom Multi Adapter

```java

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

public class ${NAME}Adapter extends RecyclerView.Adapter<RecyclerView.ViewHolder> {

    private Context mContext;
    private ArrayList<${Model_Name}> list;
    private int type;

    public ${NAME}Adapter(ArrayList<${Model_Name}> list,int type, Context mContext) {
        this.list = list;
        this.type = type;
        this.mContext = mContext;
    }

    @NonNull
    @Override
    public RecyclerView.ViewHolder onCreateViewHolder(@NonNull ViewGroup parent, int viewType) {
           View v;
        if (type == Constants.TYPE_DECOST_PUBLICATIONS) {
            v = LayoutInflater.from(parent.getContext()).inflate(R.layout.${design_Name1}, parent, false);
            return new ${ViewHolder1}ViewHolder(v);
        }
        if (type == Constants.TYPE_LATEST_DECOST) {
            v = LayoutInflater.from(parent.getContext()).inflate(R.layout.${design_Name2}, parent, false);
            return new ${ViewHolder2}ViewHolder(v);
        } else
            return null;
    }

    @Override
    public void onBindViewHolder(@NonNull RecyclerView.ViewHolder holder, final int position) {
        final ${Model_Name} model = list.get(position);
        
        if (holder instanceof ${ViewHolder1}ViewHolder) {
            final ${ViewHolder1}ViewHolder holder1 = (${ViewHolder1}ViewHolder) holder;
            holder1.bind(model);
        }
        if (holder instanceof ${ViewHolder2}ViewHolder) {
            final ${ViewHolder2}ViewHolder holder2 = (${ViewHolder2}ViewHolder) holder;
            holder2.bind(model);
        }
    }

    @Override
    public int getItemCount() {
         return (list != null ? list.size() : 0);
    }

    static class ${ViewHolder1}ViewHolder extends RecyclerView.ViewHolder {

        private TextView tv_title;

        private ${ViewHolder1}ViewHolder(@NonNull View itemView) {
            super(itemView);

            tv_title = itemView.findViewById(R.id.custom_tv_title);

        }

        @SuppressLint("SetTextI18n")
        private void bind(${Model_Name} model) {

        }
    }
        static class ${ViewHolder2}ViewHolder extends RecyclerView.ViewHolder {

        private TextView tv_title;

        private ${ViewHolder2}ViewHolder(@NonNull View itemView) {
            super(itemView);

            tv_title = itemView.findViewById(R.id.custom_tv_title);

        }

        @SuppressLint("SetTextI18n")
        private void bind(${Model_Name} model) {

        }
    }
}


```


