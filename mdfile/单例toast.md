# 单例toast

当我们处于某个场景，例如一个按钮可以触发toast的显示，当你在多次点击按钮时，会多次触发toast的显示。而调用android原生的toast的makeText的方式所生产的toast是被加到一个队列里面，然后依次执行。这样就会出现多次点击按钮触发的toast一直会按队列出现在界面上，而且即使退出了当前界面也会一直出现在手机上,而且无法手动取消，这时的用户体验变得非常的差。这时就可以使用自定义样式的toast。

```
public class ToastUtils {
    private static Toast toast = null;

    //Application初始化，避免内存泄漏
    public static void init(Application mContext) {
        if (toast != null) {
            return;
        }
        //不使用new Toast(mContext)，会出异常
        toast = Toast.makeText(mContext, "", Toast.LENGTH_SHORT);
    }

    public static void showToast(String msg) {
        if (toast == null) {
            return;
        } else {
            toast.setDuration(Toast.LENGTH_LONG);
            toast.setText(msg);
            toast.show();
        }
    }
}

```
然后哪用就哪调用方法就可以，很简单吧！