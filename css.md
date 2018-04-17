css note
============================
> #### 1. 水平居中
text-align规定了其子元素的对齐方式，一般来说，让子元素水平居中，应该设置父元素text-align:center。

> #### 2. vertical-align垂直居中
vertical-align:center垂直居中的前提是，①子元素是display:inline-block，②父元素的line-height有一个具体数值。

> #### 3. \<img src=' '/>
当设置img的src为空字符串时，有的浏览器默认行为会把图片解析成一个带有边框的空白。这时可通过设置css：

    img[src=''] {display: none}
来去掉这个空白框。
