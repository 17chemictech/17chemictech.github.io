# blog.olivie.space

GitHub Pages 站点，自定义域名 `blog.olivie.space`。

## 目录

| 路径 | 内容 |
| --- | --- |
| `/` | Olivie Blog —— Astro 静态博客（源仓库 `17chemictech/personal-blog`） |
| `/chat/` | Chat Demo —— DeepSeek API 静态聊天示例（源仓库 `17chemictech/chat-whale`） |

## 部署方式

两个子项目都在本地构建后，把产物同步到这里再推送（Pages 用 `main` 分支根目录）：

```bash
# 博客
cd ~/DeepSeek/blog && pnpm build      # → dist/
rsync -a --delete ~/DeepSeek/blog/dist/ ~/DeepSeek/pages-out/ --exclude .git --exclude CNAME --exclude README.md

# 聊天 demo
cd ~/DeepSeek/chat-whale && pnpm build  # → dist/
rsync -a --delete ~/DeepSeek/chat-whale/dist/ ~/DeepSeek/pages-out/chat/

git -C ~/DeepSeek/pages-out add -A && git commit -m "deploy: ..." && git push
```

`.nojekyll` 与 `CNAME` 必须保留在仓库根目录。
