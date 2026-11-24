# blog.olivie.space

GitHub Pages 站点（`main` 分支根目录），自定义域名 `blog.olivie.space`，HTTPS 强制开启。

**这是纯产物仓库，不要手改内容**——所有文件由源仓库的发布脚本生成。

| 路径 | 内容 | 源仓库 |
| --- | --- | --- |
| `/` | Olivie Blog（Astro 静态博客） | [`17chemictech/blog`](https://github.com/17chemictech/blog) |
| `/chat/` | Chat Demo（DeepSeek API 静态聊天示例，微信风皮肤） | [`17chemictech/chat-whale`](https://github.com/17chemictech/chat-whale) |

根目录的 `CNAME`（`blog.olivie.space`）与 `.nojekyll` 由脚本写入，必须保留。

## 发布

```bash
cd ~/DeepSeek/blog
pnpm deploy        # = bash scripts/deploy.sh
```

脚本会：构建博客 → 把博客产物放根目录、`~/DeepSeek/chat-whale/dist` 挂到 `/chat/` → 写 `CNAME`/`.nojekyll` → 对齐远端后 `rsync --delete` 覆盖本仓库工作区 → commit + push（Pages 随后自动重建，约 20–60 秒）。

只做本地同步不推送：`SKIP_PUSH=1 pnpm deploy`。

只改了聊天 demo 的话，先 `cd ~/DeepSeek/chat-whale && pnpm build`，再跑一次 `pnpm deploy`。
