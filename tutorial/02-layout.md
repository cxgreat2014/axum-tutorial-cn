# 布局

一个普通的 [axum] 项目的目录结构：

```
axum-project/
├── Cargo.toml
└── src
    └── main.rs
```

`Cargo.toml` 文件包含依赖项。例如：

```toml
[package]
name = "axum-project"
version = "0.1.0"
edition = "2021"

[dependencies]
axum = "0.5"
tokio = { version = "1", features = ["full"] }
```

`src/main.rs` 包含代码。例如：

```rust
use axum::{routing::get, Router};

#[tokio::main]
async fn main() {
    let app = Router::new().route("/", get(|| async { "Hello, world!" }));

    axum::Server::bind(&"0.0.0.0:3000".parse().unwrap())
        .serve(app.into_make_service())
        .await
        .unwrap();
}
```

## Workspace

本教程使用工作区进行示例项目。工作区使得项目的组织更加清晰，而且项目共享公用依赖项。

工作区的目录结构：

```
workspace/
├── Cargo.toml
├── hello-world
│   ├── Cargo.toml
│   └── src
│       └── main.rs
└── generate-random-number
    ├── Cargo.toml
    └── src
        └── main.rs
```

工作区的 `Cargo.toml` 包含成员。例如：

```toml
[workspace]

members = [
    "hello-world",
    "generate-random-number",
]
```

# [下一页](03-hello-world.md)

创建一个“Hello, World”应用。

[axum]: https://github.com/tokio-rs/axum
