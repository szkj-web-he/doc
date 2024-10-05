# Monorepo

### 前言：

在之前的写过的案例里。有对 video 库进行封装，通过 package.json 里的 workspaces+rollup 的 alias，我把它当作了 monorepo 管理模式。现在发现它是错的。
错误：workspaces 的配置，加上 alias,顶多算是别名，没有根本上解决，monorepo 为什么诞生的关键。

1. 它是什么？
   一种管理模式。准确说，多包管理模式。
   通俗来讲： 它相当于是将一个大包，拆成多个小包，而在发布前，他们之前又可以相关关联。
2. 它为什么会出现
   - 场景：
     公司有很多业务所需功能:video,transformAudioToText,UploadFile,IconFont,Library 等等。这些，需要管理时，通常解决方案是进行分包发布，但是存在问题， 每次发包都需要关联的那个包将所需的功能发布后，才能进行发布。但是又存在关联包发布后，调试存在一定的业务逻辑不通，又要撤包，修改，再发布。
     这个流程太过麻烦，于是 monorepo 就诞生了
