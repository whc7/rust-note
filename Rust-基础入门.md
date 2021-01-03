# 简介

Rust语言的学习曲线十分陡峭，但是发展至今，Rust已经拥有非常丰富的入门资料及完善的文档。本文旨在介绍这些资料及入门步骤。后续再对细节内容进行一一的学习讲解。

*本文尽力收纳网上能找到的个人觉得最有价值的Rust学习材料。*

入门步骤如下：

## 环境配置

万事开头难，环境配置有单独的一篇笔记

https://github.com/whc7/rust-note/blob/main/Rust-环境配置.md

## 阅读官方的手册（rust圣经）

Rust手册中文版：[Rust 程序设计语言 - Rust 程序设计语言 简体中文版](https://kaisery.github.io/trpl-zh-cn/)

按照这本手册的顺序，可以系统的了解到Rust大部分特性的基础使用方法，从构建一个hello world项目到一步一步实现一个多线程web server。

但是目前缺少了关于异步的使用介绍，也是因为目前（2021-1-3）没有稳定的官方异步库，后续细节内容我在提

## 使用Rust官方的练习库rustlings

rustlings是一系列关于rust特性的练习题，有很方便的使用方法

- 首先从github上下载官方题库及rustlings的运行库
  
  https://github.com/rust-lang/rustlings
  
  然后执行如下命令
  
  ```shell
  cd rustlings
  cargo install --path --force .
  rustlings watch
  ```
  
- rustlings watch即开始写练习题的命令之一，记住保持当前的终端开启。
  
  命令会提示当前练习题目的要求，之后打开命令对应的rust文件（无论用什么IDE）,修改保存后rustlings会自动进行检查，看练习是否完成，无误后删掉练习题目中的
  
  “**// I AM DONE**“注释，保存后rustling会自动开始检查下一道题目，根本停不下来。
  

## 学会阅读官方库文档

https://docs.rs

在练习中你可能会产生很多疑问是在之前学习中没真正搞懂的，这时可以打开上面的链接，找到rust的标准库文档，同时所有第三方库都被统一管理，可以在这个网站阅读所有你需要的文档。

- 标准库的文档在页面右上角下拉框：
  
  **Rust -> Standard Library API Reference**
  
- 其他三方库可以在搜索框中搜索
  
- 单独库的页面需要注意页面顶部**Feature flags**这个标签
  
  点进去可以看到这个库某些特性及其对应的feature flag，表示一些特性的使用是需要在toml文件中显示标示feature flag的。
  
  比如要使用futures库的ThreadPool，需要在toml文件中如下定义：
  
  ```toml
  futures = {version = "0.3.8", features = ["thread-pool"]}
  ```
  

## 进阶的学习

1. Rust Cook Book
  
  https://rust-lang-nursery.github.io/rust-cookbook/
  
  rust的实践指南。
  
2. CARGO BOOK
  
  [Introduction - The Cargo Book](https://doc.rust-lang.org/cargo/index.html)
  
  rust的项目管理器。
  
3. RUSTC BOOK
  
  [What is rustc? - The rustc book](https://doc.rust-lang.org/rustc/index.html)
  
  rust的编译器。
  
4. RUSTDOC BOOK
  
  [What is rustdoc? - The rustdoc book](https://doc.rust-lang.org/rustdoc/index.html)
  
  rust写作。
  
5. TOKIO BOOK
  
  https://github.com/dslchd/tokio-cn-doc
  
  rust中的异步，tokio一个比较成熟的第三方库，文档介绍的十分详细。
  
6. Rust宏使用
  
  [The Little Book of Rust Macros](https://danielkeep.github.io/tlborm/book/index.html)
  
  暂时没有详细的文档介绍自定义派生宏，可以在docs.rs中研究syn和quote这两个库的使用。
