

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

com.mrq.library.Toasty.Toasty.error($context$, "$message$", Toasty.LENGTH_SHORT,true).show();

com.mrq.library.Toasty.Toasty.info($context$, "$message$", Toasty.LENGTH_SHORT,true).show();

com.mrq.library.Toasty.Toasty.success($context$, "$message$", Toasty.LENGTH_SHORT,true).show();

com.mrq.library.Toasty.Toasty.warning($context$, "$message$", Toasty.LENGTH_SHORT, true).show();

```

## YoYo

```YoYo

com.mrq.library.YoYo.YoYo.with(com.mrq.library.YoYo.Techniques.Tada)
    .duration(1000)
    .repeat($repeat$)
    .playOn($textView$);

```


















