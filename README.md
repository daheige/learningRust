# Hello World

## 开发环境(VS Code)配置
### 安装Rust
* [install link](https://forge.rust-lang.org/infra/other-installation-methods.html)
* 通过`rustup`安装rust工具链，包括：
   * cargo - rust包管理工具
   * rustc - rust编译器
   * rustfmt - rust代码风格工具
   * rust-gdb - rust调式工具
### Rust代码编译与调试
   * `rustc -g main.rs`
      * 生成带调试信息的可执行文件`main`
   * `rust-gdb main`
      * 进入gdb调试界面，可以执行和C代码调试一样的命令进行rust代码的调试
      * [参考](https://users.rust-lang.org/t/rust-debuggers-question/7382)
   * `rustfmt main.rs`
      * 格式化main.rs中的代码风格
      * `rustfmt`的配置文件在`~/.config/rustfmt/rustfmt.toml`中，没有可自己建
      * `rustfmt.toml`中的定义可参考：[link1](https://github.com/rust-lang/rustfmt/blob/master/Configurations.md), [link2](https://github.com/rust-lang/rustfmt/blob/master/Configurations.md)
### 通过`cargo`管理rust工程
   * [参考](https://asquera.de/blog/2017-03-03/setting-up-a-rust-devenv/)
   * 新建Rust工程
      * `cargo init --bin vs-hello`
   * 编译工程
      * `cargo build`
   * 清理工程
      * `cargo clean`
### 通过VS Code调试Rust
   * 参考[link](https://www.forrestthewoods.com/blog/how-to-debug-rust-with-visual-studio-code/)和[例子](./code/vs-hello)
   * 安装VS Code插件
      * Better TOML
      * CodeLLDB
      * Rust
   * 配置Rust插件`settings.json`，其中关闭Rls自启动，Rls(Rust Language Server)是微软开发的Rust IDE工具。默认会去寻找Rust工程中的`Cargo.toml`文件。为了防止单文件的出错信息，关闭自启动。
```json
{
   "rust-client.rustupPath": "$HOME/.cargo/bin/rustup",
   "rust-client.autoStartRls": false
}
```
   * 配置Cargo工程中的`setings.json`
```json
{
   "rust-client.autoStartRls": true
}
```
   * 配置Cargo工程中的`launch.json`
```json
{
   "version": "0.2.0",
   "configurations": [
      {
         "type": "lldb",
         "request": "launch",
         "name": "Debug",
         "program": "${workspaceFolder}/target/debug/vs-hello",
         "args": [],
         "cwd": "${workspaceFolder}"
      }
   ]
}
```
   * 开启VSCode全局断点
```json
{
   "debug.allowBreakpointsEverywhere": true
}
```
   * 打断点并在VSCode中调试


## 分析Rust程序
* [main.rs](./code/hello/main.rs)
```rust
fn main() {
   println!("Hello, world!");
}
```


