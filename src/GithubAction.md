# github action

什么是 github action
就是自动化部署
通过 push、fork、Pull 等等行为触发自己所指定的分支，运行工作流

一个简单的 github action
只需要在.github 文件夹下创建一个[name].yaml 文件

```
name: build
on:
    push:
        branches:['main']
jobs:
    build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout 🛎️
        uses: actions/checkout@v4
      - uses: pnpm/action-setup@v4
        with:
          version: 10
      - name: Use Node
        uses: actions/setup-node@v4
        with:
          node-version: "20"
          cache: "pnpm"

      - name: Install and Build 🔧
        run: |
          pnpm install
          npm run build
```
