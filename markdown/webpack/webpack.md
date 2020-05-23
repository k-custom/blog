### webpack 
   - 本质上，webpack是一个现代Javascript 应用程序的静态模块打包器（module bundler）,当 webpack 处理应用程序时，它会递归构建一个依赖关系图（dependency graph）, 其中包含应用程序需要的每个模块，然后将所有模块打包成一个多个bundle
   - 基本打包机制
        -打包过程可拆分四个步骤：
            1. 利用babel完成代码转换，并生成单个文件的依赖
            2. 从入口开始递归分析，并生成依赖图
            3. 将各个引用模块打包成一个立即执行函数
            4. 将最终的bundle文件写入bundle.js中

   - Webpack Loader
        - loader 让 webpack 能够去处理那些非 JavaScript 文件（webpack 自身只理解 JavaScript）。loader 可以将所有类型的文件转换为 webpack 能够处理的有效模块
        - 本质上，webpack loader 将所有类型的文件转换为应用程序的依赖图（和最终的bundle）可以直接引用的模块

        - 在 webpack 配置中loader 有两个目标
            1. test 属性： 标识出应该被对应的 loader 进行转换的某个或某些文件
            2. use 属性： 表示进行转换时，应该使用哪个 loader

        - 三种方式使用 loader
            1. 配置： webpack.config.js
            2. 内联： 在每个 import 语句中显示指定 loader
            3. CLI：在 shell 命令中指定

   - Webpack Plugin
        - 插件目的在于解决 loader 无法实现的其他事情
        - webpack plugin 是一个具有 apply 属性的 JavaScript 对象， apply 属性会被 webpack compiler 调用，并且 compiler 对象可在整个编译生命周期访问。
        - 插件可以携带参数/选项，故必须在 webpack 配置中，向 plugins 属性传入 new 实例
   
   - HRM 原理


   - Webpack 性能优化


   - 构建工具选择

