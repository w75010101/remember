项目中echarts的问题
=====================
> #### 1. 可能有bug的api
触发整个render区域的事件:

    [echartsInstance].getZr().on([event], fun)
可以为整个渲染区域添加事件，但是回调函数接受的参数不同，就地图而言，有地图的地方参数参考官方文档，没有地图的地方则只会传入事件对象。

> #### 2. type: 'geo'时，配置项问题
在对地图上的单个国家配置样式时，发现问题：

    //...
    let option = {
       type: 'geo',
       regions: [
       //存放想要单独配置的国家
          {
             name: '中国',//与world.json中的配置的name一致
             itemStyle: {
                areaColor: '#00f',//官网配置是错误的，这里的配置和整体地理图配置一样
                color: '#ff0'
             }
          }
       ]
    }
