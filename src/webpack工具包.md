这次总结点啥呢？
说说集成的 react+webpack+ts+babel 的工具包吧

# webpack 工具包

功能: 它集成了 react+ts 的处理，集成了对 sass 文件的处理，还有各种字体，图片的处理
路径别名是~/src/**/**

原因： 在工作一段时间后，因为产品的需求递增，项目也跟着递增，发现每次都要在 package.json 里下一大堆的依赖项为同样的项目添加配置，于是就想着，有什么办法可以将这些项目所共用的 webpack 配置集成下来,简化工作时长

1. 在工具包中，利用 package.json 里的 bin 属性生成专属的指令键"datareachable"在映射到所需要的 node 调用 webpack 的配置层
2. 指定在项目中 package.json 里 script 所执行的脚本，进而和配置层的命令相匹配
3. 在工具包中，将集成的配置项想写好，减少暴露在项目里的依赖，弱化开发难度
4. 利用 babel 处理/.(j|t)sx?/的文件;利用 resolve-url-loader 解决工具包和项目里的文件引用路径不匹配的问题；利用 postcss-loader,sass-loader 预编译处理。用这些基础配置来减少项目里所需的额外配置
5. 在 node 调用 webpack 层里，新增读取项目里根目录下的 datareachable.config.js 文件来合并配置项，从而达到自定义配置
6. 读取静态文件，达成约定，Public 文件夹下的所有文件都不会进行处理，会直接拷贝到打包后的文件夹里
7. 将包发布到公司下，提供前端使用
