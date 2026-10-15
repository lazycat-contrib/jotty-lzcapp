# Jotty - LazyCat App

[Jotty](https://github.com/fccview/jotty)（轻量强大的文件化笔记与清单管理）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/fccview/jotty` 镜像经 `ghcr.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag（`channel: stable`），发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- Next.js 单容器，非 root 运行（`user: 1000:1000`）
- 三数据卷：`data`（笔记/清单文件）、`config`（配置）、`.next/cache`（构建缓存）
- 首次打开跳转 `/auth/setup` 创建管理员账号（首个用户即管理员）；支持 OIDC/SSO（参考上游 howto/DOCKER.md）
- 健康检查用 node fetch `/api/health`（镜像不含 curl/wget）

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

AGPL-3.0（上游）
