# Live-Templates-

## [ColorPicker](https://github.com/ibrahim-mrq/library#colorpicker "ColorPicker")

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
