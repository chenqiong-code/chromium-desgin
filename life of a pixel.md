# 为什么会有Layer?

## 背景

在使用devtool Layers面板调试tieba首页时，会看到在未进行滚动的情况下页面会有6个layer，下篇文章会具体分析5个layer造成的原因以及改进的地方，这篇文章解释Layer的由来，为下篇文章做准备。
<img width="956" alt="截屏2021-09-08 上午8 57 09" src="https://user-images.githubusercontent.com/62834754/132428982-51d9d110-21be-4c9c-baa2-65d30d179a3a.png">


## 声明

本篇文章的绝大多数内容来自于chromium团队的ppt https://docs.google.com/presentation/d/1boPxbgNrTU0ddsc144rcXayGA_WF53k96imRH8Mp34Y/edit#slide=id.ga884fe665f_64_6

## content
<img width="947" alt="截屏2021-09-08 上午8 57 55" src="https://user-images.githubusercontent.com/62834754/132428997-3b13a15f-942e-48ad-8b57-7afa46eadd3d.png">

看图说话：

- content 是指在Chromium C++代码库中的的命名空间、这个命名空间就是对应上图红色边框包裹的部分
- Blink是渲染器进程中的代码子集，在content命名空间下
- Blink实现了web平台API(e.g., DOM Level3)以及web规范的语义(e.g., ECMAScript spec)
- 渲染发生在sandboxed process，包含cc (content collator)
- content 可以理解为在网页内的代码或者Web应用程序的前端
- content source code是渲染器的输入

## pixels

- 渲染器的输出是屏幕上的像素
- 一些库(e.g., openGL)允许你执行“在这些坐标处将三角形绘制到虚拟像素缓冲区中”之类的操作
- chromium引入了这些库

## renderer goals
<img width="954" alt="截屏2021-09-08 上午8 58 30" src="https://user-images.githubusercontent.com/62834754/132429009-5d927985-7b2b-422a-92e5-41588fd1117a.png">
<img width="964" alt="截屏2021-09-08 上午8 58 40" src="https://user-images.githubusercontent.com/62834754/132429014-7ed26855-1521-4440-9c63-6ff6e0e25dd8.png">

## parsing

<img width="950" alt="截屏2021-09-08 上午8 58 50" src="https://user-images.githubusercontent.com/62834754/132428954-1c789d3c-fdbd-45cc-9229-5caafc400cce.png">


The JavaScript engine (V8) exposes DOM web APIs as thin wrappers around the real DOM tree through a system called "bindings"

## TODO:把照片贴过来

