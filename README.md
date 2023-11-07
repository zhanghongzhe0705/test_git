# 项目分支及环境切换

>deve:ipidea国内站正式服，如无特殊情况，更新正式服没问题再提交本分支
>master:ipidea国内站备份
>develop:ipidea国内站竞价推广单页面项目
>ceshipage:原国外官网测试服，现已弃用
>text:现国外站官网测试服
>ceshiucenter:国外站个人中心测试服
>page:国外站官网正式服
>ucenter:国外站个人中心正式服

>国内站全局搜索netapi.321174，可以看到一个测试接口一个生产接口，注释不同的接口即可切换测试或生产环境。
>国外站全局搜索api.glo.ipidea，同国内站操作，另外多一步修改store里的跳转路径，因为国外站分成了两个地址。

# nuxt-websit

> My superior Nuxt.js project

## Build Setup

``` bash
# install dependencies
$ npm run install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).


```



## 4. nuxt中使用百度地图
1. 在nuxt.config.js中，配置
```
    head: {
        title: process.env.npm_package_name || '',
        meta: [
            { charset: 'utf-8' },
            { name: 'viewport', content: 'width=device-width, initial-scale=1' },
            { hid: 'description', name: 'description', content: process.env.npm_package_description || '' }
        ],
        link: [
            { rel: 'icon', type: 'image/x-icon', href: '/favicon.ico' }
        ],
        script: [ // 这里添加百度地图的js文件
            { src: "https://api.map.baidu.com/api?v=2.0&ak=9UxhL8yiE89j3ryPL2G25msjPFzTnDGd" }
        ]
    },
```

2. 在文件中使用
```
    <div class="address" id="allmap"></div>

    mounted() {
        this.init();
    },

    methods: {
        init() {
            var map = new BMap.Map("allmap");
            var point = new BMap.Point(106.504330,29.619820);
            var marker = new BMap.Marker(point); // 创建标注
            map.addOverlay(marker); // 将标注添加到地图中
            map.centerAndZoom(point, 19);
            var opts = {
                width: 307, // 信息窗口宽度
                height: 100, // 信息窗口高度
                title: "" // 信息窗口标题
            };
            var infoWindow = new BMap.InfoWindow(
                "",
                opts
            ); // 创建信息窗口对象
            map.openInfoWindow(infoWindow, point); //开启信息窗口
            map.enableScrollWheelZoom(true);
        },
    }
```
