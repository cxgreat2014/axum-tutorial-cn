# 介绍

## 什么是 Axum？

[axum] 是一个注重人体工程学和模块化的 Web 应用框架。

### 模块化

[axum] 是基于 [tower] 抽象构建的。这些抽象：

- 是协议无关的，这意味着你可以为多个协议（如 http 和 grpc）使用相同的代码。
- 有内置的中间件和工具，可与 [axum] 一起使用。
- 允许更低级别的访问。这使得创建用于与 [axum] 工作的库变得容易。你可以在[这里][ecosystem]找到有用的库。

## 为什么使用 Axum？

[axum] 不会重新发明所有东西。

通常，一个[axum] 应用程序使用：

- 用于异步运行时和实用程序的 [tokio]，
- 用于 HTTP 服务器的 [hyper]。
- 用于中间件和实用程序的 [tower] 和 [tower-http]。

所有这些库都经过了非常好的测试、维护和生产使用。

# [下一页](02-layout.md)

关于 [axum] 项目布局的概述。

[axum]: https://github.com/tokio-rs/axum
[ecosystem]: https://github.com/tokio-rs/axum/blob/main/ECOSYSTEM.md
[hyper]: https://github.com/hyperium/hyper
[tokio]: https://github.com/tokio-rs/tokio
[tower]: https://github.com/tower-rs/tower
[tower-http]: https://github.com/tower-rs/tower-http
[tokio team]: https://github.com/tokio-rs
