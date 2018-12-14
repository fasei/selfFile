---
title: docker删除镜像
tags: [android,webView]
date: 2018-04-10
categories: android
---

对于移动端的混合模式开发，一般都会涉及到WebView这一控件，在该控件加载网页的过程中，多多少少都会遇到加载网页失败等情况，那么也该做个记录，记录下这些坑。

<!--more-->

## 404错误

```

  webView.setWebViewClient(new WebViewClient() {

            @SuppressWarnings("deprecation")
            @Override
            public void onReceivedError(WebView view, int errorCode, String description, String failingUrl) {
                super.onReceivedError(view, errorCode, description, failingUrl);
       //TODO
            }

            @TargetApi(android.os.Build.VERSION_CODES.M)
            @Override
            public void onReceivedError(WebView view, WebResourceRequest req, WebResourceError rerr) {
       //TODO

            }
```

这种错误是挺奇怪的，上述onReceiveError根本不会调用！搜索了好久，见网上有人这么解决：

```

 webView.setWebChromeClient(new WebChromeClient() {
            @Override
            public void onReceivedTitle(WebView view, String title) {
                super.onReceivedTitle(view, title);
                CharSequence pnotfound = "404";//或者找不到页面
                if (title.contains(pnotfound)) {
                    view.setVisibility(View.INVISIBLE);
                }
            }
        });
```

## 本地网页写法：

在asset中放网页
```
<html>
<body>
<div>
    <table width="50%" height="50%" >
        <tr>
            <td>
                <p style="text-align:center;"><img src="time_out.png"></p>

            </td>
        </tr>
    </table>
</div>
</body>
</html>
```


然后异常捕获处理

```
public static final String NOT_FOUND_PAGE = "file:///android_asset/not_found.html";

 webView.setWebChromeClient(new WebChromeClient() {
            @Override
            public void onReceivedTitle(WebView view, String title) {
                super.onReceivedTitle(view, title);
                CharSequence pnotfound = "404";//或者找不到页面
                if (title.contains(pnotfound)) {
                    view.stopLoading();
                    view.loadUrl(NOT_FOUND_PAGE);
                }
            }

        });
```

至此结束啦~~
