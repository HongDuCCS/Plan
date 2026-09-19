# CCS 维护手册

> 版本：2026-09
> 适用对象：CCS 维护人员
> 原则：任何人拿到这份文档，都能接管 CCS 的技术维护。

---

## 第一章  技术栈总览

| 层       | 技术                                           | 部署目标                   |
| -------- | ---------------------------------------------- | -------------------------- |
| 前端     | Vue 3 + TypeScript + Vite + Pinia + Vue Router | Cloudflare Pages（免费）   |
| 后端     | Hono + Cloudflare Workers                      | Cloudflare Workers（免费） |
| 数据库   | Cloudflare D1（SQLite）                        | 免费 5GB                   |
| 图片存储 | Cloudflare R2                                  | 免费 10GB/月               |
| 包管理   | pnpm（monorepo）                               | —                          |

详细技术文档见仓库根目录的 `README.md`。

---

## 第二章  本地开发

### 2.1 环境要求
- Node.js 18+
- pnpm
- Cloudflare 账号

### 2.2 启动步骤

```bash
pnpm install

# 1. 启动后端（本地 D1 数据库）
pnpm db:migrate:local
pnpm dev:api            # http://127.0.0.1:8787

# 2. 启动前端（/api 自动代理到 8787）
pnpm dev:web            # http://127.0.0.1:5173