# 简介

*本文摘抄自《Rust编程之道》*

Rust是强类型且类型安全的静态语言，支持参数化多态和Ad-hoc多态（类似C中的模版特化），对应Rust的泛型和trait。

## 有大小类型

Rust通过Sized trait决定类型是编译期大小确定的类型（如i32）或是少数动态大小的类型（如**str**），对于动态大小的类型，提供引用类型'&'，类似指针。

## 零大小类型（ZST）

如foo()函数的返回值、struct A{}空结构体。零大小类型不占用内存空间，还可以用于只需要迭代次数的场合，如Vec<()>类型，Vec内部迭代器会对ZST类型进行优化，获得更高的性能。

## 底类型

也就是never类型，rust的底类型是所有类型的子类型。用于

- 发散函数：也就是程序异常终止，比如panic；
  
- 流程跳转：break和continue；
  
- 无限循环：如没有终止条件的loop；
  
- 空枚举：不知道干嘛用，应该就是never
  

猜测应该只是为了语法解析方便增加的类型，实际作用不大。

## 类型推导

rust支持部分范围的类型推导，省去一些定义类型的工作，类似auto。显示标注类型有两种方式，如下：

```rust
let a = "8";
let a: i32 = a.parse().unwrap();
let a = a.parse::<i32>().unwrap(); // turbofish，也叫特化
```

## 泛型

编译期会把泛型块进行单态化，比如

```rust
// code
let a: &str = "a";
let b: u8 = 1;
foo(a);
foo(b);

// 泛型函数
fn foo<T>(x: T)
    where T: Display {
    println!("foo: {}", x);
}

// 单态化
fn foo(x: u8) {
    println!("foo: {}", x);
}

fn foo(x: &str) {
    println!("foo: {}", x);
}
```

这就造成编译后的二进制文件变大，如果对程序大小有要求，可以选择重新设计，比如把str和u8都用[u8]来表示。

泛型返回值可以自动推导，类似**turbofish**（特化）和冒号指定类型的形式可以自动转化。

## trait类型、类型转换

篇幅较长，放在下集
