# 说明

    一个vue2 + vuex + vue-resourse的项目，适合作为入门练习。这是个我练习vuex的小项目，改写github上的一个项目，
    
    用我自己的理解，实现了同样的功能。里面详细的注释了部分代码。

    如果对您有帮助，您可以点右上角 "Star" 支持一下 谢谢！ ^_^

    或者您可以 "follow" 一下.

    如有问题请直接在 Issues 中提，或者您发现问题并有非常好的解决方案，欢迎 PR 👍


# 帮助文档：

关于VUEX的一些文档，感觉写的通俗易懂，适合新手阅读。

Vuex，从入门到入门   

https://zhuanlan.zhihu.com/p/24357762

vuex2.0 基本使用(2) --- mutation 和 action

http://www.cnblogs.com/SamWeb/p/6543931.html


# 补充说明

本项目我尽可能的简单明了，项目涉及到路由，其实更高级点，你可以在路由上配置按需加载，如

{
        path: '',
        
        component: r => require.ensure([], () => r(require('../page/home')), 'home')
}

但是，为了项目更明了，我用了最原始的也最直接的方法。

里面也涉及到less的一些小问题以及引用，为了让新手更容易理解学习，我在不同的页面用了不同的引用方式，但是效果是一样的。

里面也有一些ES6语法，但是用的少，但是对vue，还是用es6的好，你可以去查查资料。


## 运行

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build


For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).




