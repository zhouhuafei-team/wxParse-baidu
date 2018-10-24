感谢icindy开源贡献的微信小程序富文本插件 https://github.com/icindy/wxParse 本项目根据此插件微调而来。

# 如何使用
* 和https://github.com/icindy/wxParse 的使用方式基本相同
    - 在对应swan文件中引入 ```<import src="../../plugins/wxParse/wxParse.swan"/>``` 。
    - 在对应swan文件中使用 ```<view class="wxParse-wrap"><template is="wxParse" data="{{ {wxParseData:detailInfo.nodes} }}"></template></view>``` ，注意：此处有不同点，这里是三个大括号 ```{{ {} }}``` 。
    - 在对应css文件中引入 ```@import url(../../plugins/wxParse/wxParse.css);``` 。
    - 在对应js文件中引入 ```import WxParse from '../../plugins/wxParse/wxParse.js';``` 。
    - 在对应js文件中使用 ```WxParse.wxParse('detailInfo', 'html', `<div>这里是富文本要渲染的html结构</div>`, this);``` ，this是Page对象。

# 修改的内容
* .wxml文件更换为.swan文件，并
    - 对内部的模板语法关键字进行替换。
    - {{item}} 替换成了 {{ {item} }}。
    - wx:for 替换成了 s-for 等。
    - 去掉了第21行image标签上重复的mode属性。
* .js中wx. 换成 swan.
* .wxss更换为.css，并
    - 去掉了view选择器的overflow: auto;
    - 给view选择器加了个父亲，变成了```.wxParse-wrap view{word-break:break-all;}```，防止影响太广。使用时，只需给富文本容器加个class="wxParse-wrap"就行了。
