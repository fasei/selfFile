# Android MarginLeft与MarginStart的区别

在写layout布局的时候，我们会发现有这样几个比较相似的属性：

MarginStart **VS**   MarginLeft

MarginEnd **VS**  MarginRight

这些属性的区别是什么?  根据api注释，我们得知MarginStart指的是控件距离开头View部分的间距大小，MarginLeft则指的是控件距离左边View部分的间距大小，MarginEnd和MarginRight同理。

一般情况下，View开始部分就是左边，但是有的语言目前为止还是按照从右往左的顺序来书写的，例如阿拉伯语，在Android  4.2系统之后，Google在Android中引入了RTL布局，更好了支持了由右到左文字布局的显示，为了更好的兼容RTL布局，google推荐使用MarginStart和MarginEnd来替代MarginLeft和MarginRight，这样应用可以**在正常的屏幕和由右到左显示文字的屏幕上都保持一致的用户体验**。

**以下内容摘自他人翻译的中文Android 4.2API:**
> Android 4.2引入了由右到左文字的全面本地支持布局。在本地RTL支持下，您可以为所有用户带来完美的应用体验，不论他们的文字书写方向
> 是由左至右还是由右至左。

当用户切换系统语言到由右至左书写方式时，系统提供自动的应用UI布局和所有可视组件的镜像，包括文字元素的显示和输入。

您的应用仅需极少改变即可支持RTL布局镜像。如果您的应用支持这一特性，只要在您应用的manifest文件中将所有的”left/right”布局属性改变为对应的”start/end”即可。系统就会根据需要处理您UI了。
                