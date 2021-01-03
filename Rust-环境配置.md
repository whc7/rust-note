# 简介

rust基本环境大致可以包括rustup、cargo和IDE的配置，可以大致分为以下三步：

1. 下载rustup安装rust基础环境：
  
  一个命令行工具，负责rust工具链的下载安装，用于不同平台不同版本rust基础库的管理，cargo也包含在基础工具链中。
  
2. 配置镜像源
  
  国内无法友好访问rust资源的url，rustup会报链接错误。同时也无法正常访问crate包的资源url，造成cargo（rust的包管理器）无法正常安装第三方库。
  
3. 为rust配置IDE
  
  目前我比较推荐两种方式，分别通过Intellij IDEA和VS Code。
  

## rust安装

rustup下载页面：https://www.rust-lang.org/tools/install
下载rustup可以参考官网指导，不同环境有不同都下载方式。下载完成后执行

```shell
rustup install
```

即可参考步骤安装rust及其包管理器cargo，**注意安装提示的环境变量配置**，会影响后续cargo及第三方库的安装位置，可能会占用大量空间。注意此时按照步骤安装可能会提示网络错误，那么你就需要配置国内镜像源。

## 配置国内镜像源

本人亲测（2021-1-3）清华大学镜像源非常好用，包含rustup和cargo的镜像，rustup用于**安装rust**，cargo用于**第三方库**。

rust的第三方库有个独特的名字——**crate**，cargo镜像即配置crate.io的镜像资源

清华大学rustup镜像源配置参考：[rustup | 镜像站使用帮助 | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/help/rustup/)

清华大学cargo镜像源配置参考：[crates.io-index.git | 镜像站使用帮助 | 清华大学开源软件镜像站 | Tsinghua Open Source Mirror](https://mirrors.tuna.tsinghua.edu.cn/help/crates.io-index.git/)

## IDE配置

Intellij IDEA配置：安装两个插件toml、rust即可

VSCode配置较为复杂，分为以下步骤

1. rustup安装rust-src、rust-analysis、rls
  
  - rls即rust language server，可以和VS Code的LSP进行交互，为编辑器提供语法支持。
    
  - rust-analysis可以检测代码错误，可以在编译前在编辑器中高亮语法错误，这对rust这种编译十分严格的语言十分友好。
    
  - rust-src即rust的标准库源码，源码中包含丰富的注释，非常有利于定位问题。
    
2. VS Code安装Rust、rust-analyzer插件
  
  分别与以上安装的rust工具进行配合。
  
3. VS Code安装Bracket Pair Colorizer 2、Better Toml、crates插件
  
  可选步骤，用于提升编码体验。纯属个人喜好，具体功能不再介绍。
  

## 其他问题

暂时留空，rust是个很活跃的语言，版本更新迭代速度很快，我尽量跟上。
