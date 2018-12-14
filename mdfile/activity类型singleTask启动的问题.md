# textview常用功能

## textview文字滑动
这个功能实现起来很简单，只需要两步就可以完成。具体如下：
1. 在xml布局声明textView的时候，我们设置它的scrollbars属性为vertical；
```
<TextView
        android:id="@+id/textView1"
        android:layout_width="match_parent"
        android:layout_height="200dp"
        android:layout_weight="2.89"
        android:scrollbars="vertical"
        android:textColor="#ffffffff"
        android:text=" "/>

```
2. 在java代码中使用textView时，调用textView的setMovementMethod方法即可。

```
@Override
protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.location);
    tv = (TextView) findViewById(R.id.textView1);
    tv.setMovementMethod(ScrollingMovementMethod.getInstance());
}
```

## textview滑动到底部
```
 String text = "showText:\r\n";
        for (Student stu : sss) {
            text += stu.toString() + "\r\n";
        }
        text += "end.";
        showText.setText(text);
        int offset = (showText.getLineCount()) * showText.getLineHeight() + showText.getPaddingTop() + showText.getPaddingBottom();

        Log.d("ObjectBoxActivity", "offset:" + offset + ",getHeight" + showText.getHeight());

        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.JELLY_BEAN) {
            Log.d("ObjectBoxActivity", "showText.getLineCount():" + showText.getLineCount() + ",showText.getMaxLines()" + showText.getMaxLines());

            if (showText.getLineCount() > showText.getMaxLines()) {
                Log.d("ObjectBoxActivity", " showText.scrollTo");

                showText.scrollTo(0, offset - showText.getHeight());
            } else {
                showText.scrollTo(0, 0);
            }
        }

```
