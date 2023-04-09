# Hello World

将项目名称添加到工作区。

```toml
[workspace]

members = [
    "hello-world", # <--
]
```

创建项目。

```
cargo new hello-world
```

## 依赖项

示例 `Cargo.toml`：

```toml
[package]
name = "hello-world"
version = "0.1.0"
edition = "2021"

[dependencies]
axum = "0.5"
tokio = { version = "1", features = ["full"] }
```

这些依赖项是创建最小的 [axum] 应用程序所必需的。

[tokio] 是一个非常流行的用于处理异步代码的库。[rust] 没有默认的异步运行时，这使得选择留给了用户。[axum] 仅支持 [tokio] 运行时。但是不用担心，[tokio] 提供了您可能需要的所有异步库。

## 代码

```rust
use axum::{routing::get, Router};
use std::net::SocketAddr;

#[tokio::main]
async fn main() {
    // 将所有请求路由到匿名处理程序的“/”端点。
    //
    // 处理程序是一个异步函数，返回实现了 `axum::response::IntoResponse` 的对象。

    // 可以使用闭包或函数作为处理程序。

    let app = Router::new().route("/", get(handler));
    //        Router::new().route("/", get(|| async { "Hello, world!" }));

    // 服务器将绑定到的地址。
    let addr = SocketAddr::from(([127, 0, 0, 1], 3000));

    // 使用 `hyper::server::Server`，该服务通过 `axum::Server` 重新导出以提供该应用程序。
    axum::Server::bind(&addr)
        // Hyper 服务器使用 make service。
        .serve(app.into_make_service())
        .await
        .unwrap();
}

async fn handler() -> &'static str {
    "Hello, world!"
}
```

## 运行

在工作区目录中执行此命令：

```
cargo run --bin hello-world
```

在浏览器中输入 `http://localhost:3000`。

# [下一页](04-generate-random-number.md)

创建一个应用程序，它从查询参数中响应一个随机数字。

[axum]: https://crates.io/crates/axum
[rust]: https://www.rust-lang.org
[tokio]: https://crates.io/crates/tokio
