Vue note
===================


> #### 1. v-for的key

#### 当Vue.js用v-for正在更新已渲染过的元素列表时，它默认用“就地复用”策略。如果数据项的顺序被改变，Vue将不会移动DOM元素来匹配数据项的顺序，而是简单复用此处每个元素，并且确保它在特定索引下显示已被渲染过的每个元素。


也就是说，不加key时，Vue无法侦查每一个内容对应的dom，所以当渲染的数组数量上改变时，内容很容易发生错乱。所以


#### 建议尽可能在使用 v-for 时提供 key，除非遍历输出的DOM内容非常简单，或者是刻意依赖默认行为以获取性能上的提升。



> #### 2. Vue项目中使用sass时
1. 使用方法：

①安装sass-loader和node-sass，②在使用sass的style标签上添加attribute：lang='sass'或者lang='scss'，如果要外置scss文件，需要配置loader。

    {
        test: /\.scss$/,
        loaders: ["style", "css", "sass"]
    },
    

> #### 3. 异步组件
在做大屏工具show组件时，由于内部要显示的模块信息全部需要后台返回，所以必须采用异步组件的形式。

    <template>
        <div>
            <components v-for='comArr' :is='showComArr.id' :style='{
            ///
            }'></components>
        </div>
    </template>
    //...
    <script>
    data () {
        return {
            comArr: [],//这个数组用来存放取回的组件信息。
            showComArr: []//防止在组件获取完成前渲染dom而造成无法找到模块信息而报错
        }
    },
    mounted () {
        this.comArr = [模块信息数组];
        let comObj = {};
        this.comArr.forEach((item) => {
            comObj[item.id] = _ => import(item.url);
        })
        this.$options.components = comObj;
        this.showComArr = this.comArr;//要确保所有组件获取完毕后再去渲染dom
    }
    </script>