# Gitbook 介绍

最近在写小组的论文，那就免不了会涉及到团队编辑文档。本来打算是开一个 pages 然后协作共享出来一起改，但是目前小组的机器情况是 2Win+2Mac，虽然 pages 目前也支持网页版的了，然而本地环境的使用体验还是会比网页版的好很多。还有一个要考虑的问题就是这种文档内(pages/word)的编辑很难做到版本控制，万一一不小心一个剪刀手，好吧还是不要毒奶。

经过考虑，后来决定选型协同编辑环境为`Git+Markdown`,为什么这么选主要有以下几个方面的思考。

1. 可以利用 git 的版本控制，每次 commit 的记录都可以找得到，不用担心内容的丢失。
2. 组内 Review 起来方便，只要其他成员 push 之后都会有邮件提醒，可以看到成员具体改动的地方在哪里。
3. 本地编辑时不需要网络环境 (相对于文档在线协同编辑) 。
4. 由于共用一个 repo，组间分享的各种资料也可以放上来。
5. 可以让大家熟悉一下这两个工具，上手简单而且好用。
6. md 格式的写作让大家更加关注内容本身，而不用太在意排版。

但是这么做也会带来一些弊端

第一就是如果是论文格式排版有要求的话，md 最后转 pdf 的话很难做的到，经过取舍是编辑完成后，最后一起开个 pages 文档协同合进去(pages 支持 Katex 公式，word 不行)。

第二就是如果大家一起编辑一个 md 文件的话，每次 push 都必然会产生冲突，解决办法就是拆分 md 文件，把每个人负责的内容的部分单独抽出来成单独的 md 文件，降低耦合。

第三在 vscode 里编辑的时候是没有英文的拼写和语法检查的，合进 pages 的时候一段话 6、7 个拼写错误也不是没可能的。。。
(后来发现 vscode 里拼写检查可以用`Code Spell Checker`或者`SpellRight`插件)

在最后生成 pdf 这一步觉得手动去合并每个 md 文件效率太低了，然后找了一下发现了`Gitbook`这个使用 `Git` 和 `Markdown` 来构建书籍的工具。输出的格式有很多种:PDF，ePub，mobi，或者输出为静态网页。

## 环境要求

NodeJS(v4.0.0 及以上)

### Mac

```bash
npm install gitbook-cli -g
```

刚开始在生成 pdf 的时候发现构建的时候总是会卡死，后来发现在**安装 calibre 的时候要记得选 3.X 版本**的
