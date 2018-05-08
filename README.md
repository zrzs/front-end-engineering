# （一）前言

自从前后端分离以来，“前端工程化”已经是前端领域的高频词汇。那么什么是“前端工程化”，众说纷纭。

随着 Node.js 的兴起，诞生了如 gulp、grunt、webpack 等一批自动化工具，大大提升了前端在自动化、工程化等方面的效率，并降低了成本。

大体的来说，前端工程化有两层含义：

+   广义的前端工程化

    前端工程是软件工程的一个子类，指的是将软件工程的方法和原理运用在前端开发中, 目的是实现 **高效开发**，**有效协同**，**质量可控**。

+   狭义的前端工程化

    前端工程是指将 **开发阶段** 的代码转变成 **生产环境** 的代码的 一系列步骤。

    主要包括 **构建 , 分支管理 , 自动化测试, 部署** 等。

# （二）前端工程化的特点

+   自动化
+   规范化
+   傻瓜化

# （三）前端工程化在前端开发流程的体现

**自动化** 是前端工程化的重要特征。我们通过开发一些工具，将重复性工作自动化，以提高开发、协作效率。

## 项目初始化

项目初始化，一般是初始化项目目录文件，对前端而言，一般是如下的目录结构：

```
pages/
    index/
    detail/
package.json
.gitignore
README.md
```

这个动作完全可以自动化，通过工具生成标准模板。

工具介绍：[bio-cli](https://github.com/weidian-inc/bio-cli) `init` 命令

## 本地开发

前端使用的技术栈多种多样，如 vue/react/zepto 等，样式编辑有 less/sass/原生 css 等，js 有 es5/es6 等，而这种情况遇到的困难，就是如何配置各种工具才能产出浏览器可以识别的代码。

配置的过程是繁琐的，这个过程我们也需要 **自动化**。

工具介绍：[bio-cli](https://github.com/weidian-inc/bio-cli) `run` 命令

## 数据 Mock

前端和后端由于节奏不同，但前端有时又对接口依赖，怎么办呢？数据 Mock 就有用了。

前后端数据格式在约定好后，前端同学在开发阶段接入 mock 数据，等到接口准备好后，转为真实数据即可。

现在社区有很多工具可以 Mock 数据，推荐几个：

+   [easy-mock](https://easy-mock.com/)
+   [bio-cli](https://github.com/weidian-inc/bio-cli) `mock` 命令

## 代码规范

团队协作，每个人的代码风格都不一样，除了个别开发者会自行配置代码检查，绝大部分同学很少有时间和动力为自己配置代码检查工具。

这时，团队协作就面临以下问题：

+   生产环境的代码未经漏洞审查
+   即使通过漏洞审查，代码风格也不同，团队成员间的代码维护成本较高

我们将代码检查工具化，极大简化成本。

有两种方式统一代码风格并检查漏洞：

+   开发阶段即统一代码风格
+   提交到 git 仓库统一代码风格，开发阶段不统一

两种方式都可以，看团队需求。

工具介绍：[bio-cli](https://github.com/weidian-inc/bio-cli) `lint` 命令

## 分支管理

现在大多数团队使用 git 进行代码管理。

在开发阶段使用开发分支，生产发布**自动** `merge master` 合并主干。

## 自动化测试

+   本地开发阶段进行自动化测试

    通过工具，将本地复杂的测试准备工作自动化，以便于在本地进行自动化测试。

+   线上部署阶段进行自动化测试

    线上部署阶段，很容易进行自动化测试的中心化管理，如果有项目没有写测试用例，中心化平台可以做各种操作，如暂停部署等。

本地开发和线上部署两个阶段的自动化测试，需要有机结合起来，保证测试环境的一致性。

工具介绍：[bio-cli](https://github.com/weidian-inc/bio-cli) `test` 命令

## 部署

部署阶段，因为是中心化的，所以更容易进行各种检测操作，以保证线上稳定。

它可以：

+   自动拉取项目代码
+   代码规范检测（需和本地开发阶段保持一致）
+   检查项目分支是否已合并 master，如没有，则暂停部署。避免进行回归测试。
+   自动执行测试用例
+   自动编译打包
+   健全的错误捕获机制，避免将问题代码发布到线上

# （四）工具介绍

## webpack

webpack 的变化非常快，目前我们的尝试版本是 3.10.0。

+   使用

    +   [项目个性化配置策略](./docs/项目个性化配置策略.md)(2017)
    +   [用纯 [webpack 结构] 替代 [gulp + webpack 结构] 开发脚手架](./docs/用纯[webpack结构]替代[gulp+webpack]结构.md)(2017)
    +	[脚手架与业务目录的目录结构浅析](./docs/脚手架与业务目录的目录结构浅析.md)(2017/08/23)
    +   [解决 webpack/webpack-dev-server 监听文件时频繁触发编译和回调的问题](./docs/解决webpack+webpack-dev-server监听文件时频繁触发编译和回调的问题.md)(2017)
    +   [webpack 经验谈](./docs/webpack经验谈.md)(2017)
    +   [启动一个 vue 项目](./docs/启动一个vue项目.md)(2017)

+   分析

    +   实现一个简单的 webpack：https://github.com/youngwind/fake-webpack

# 资料

+   [webpack源码学习系列之一：如何实现一个简单的webpack](https://github.com/youngwind/blog/issues/99)
+   [ 深入剖析 webpack 打包生成的一大堆代码到底是啥](http://blog.csdn.net/haodawang/article/details/77126686)
