感谢icindy开源贡献的微信小程序富文本插件 https://github.com/icindy/wxParse 本项目根据此插件微调而来。

# 如何使用
* 和https://github.com/icindy/wxParse 的使用方式基本相同
    - 在对应swan文件中引入并使用。注意：data处有不同点，是三个大括号。
    ```
    <import src="../../templates/wxParse/wxParse.swan"/>
    <view class="wxParse-wrap">
        <template is="wxParse" data="{{ {wxParseData:detailInfo.nodes} }}"></template>
    </view>
    ```
    - 在对应css文件中引入。
    ```
    @import url(../../templates/wxParse/wxParse.css);
    ```
    - 在对应js文件中引入并使用。
    ```
    import WxParse from '../../templates/wxParse/wxParse.js';
    WxParse.wxParse('detailInfo', 'html', `<div>这里是富文本要渲染的html结构</div>`, this);
    ```

# 修改的内容
* wxParse.wxml文件更换为wxParse.swan文件，并
    - 对内部的模板语法关键字进行替换。
    - {{item}} 替换成了 {{ {item} }}。
    - wx:for 替换成了 s-for 等。
    - 去掉了第21行image标签上重复的mode属性。
    - 第21行```mode="widthFix"```换成了```mode="aspectFill"```。
    - 第21行```style="width:{{item.width}}px;"```换成了```style="width:{{item.width}}px;height:{{item.height}}px;"```
* wxParse.js中wx. 换成 swan.
* wxParse.wxss更换为wxParse.css，并
    - 去掉了view选择器的overflow: auto;
    - 给view选择器加了个父亲，变成了```.wxParse-wrap view{word-break:break-all;}```，防止影响太广。使用时，只需给富文本容器加个class="wxParse-wrap"就行了。
