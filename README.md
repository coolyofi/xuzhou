# 徐州 3 天 2 夜 旅行路线

这是一个静态的单文件网站，内容来自桌面上的 `xuzhou_trip_site.html`。已经把所有样式和脚本内联，准备好直接发布到任何支持静态文件的服务。

## 如何上线

1. **GitHub Pages**（推荐）
   - 将本仓库 push 到 GitHub。
   - 在仓库设置中启用 **Pages**，选择 `main` 分支的 root 目录作为源。
   - 刷新设置页面后几分钟会生成一个可访问的 URL，例如 `https://<your-username>.github.io/<repo>`。

   如果想自动部署，可添加下面的 workflow（`.github/workflows/pages.yml`）：
   ```yaml
   name: Deploy to GitHub Pages
   on:
     push:
       branches:
         - main
   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v3
         - uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./
   ```

2. **Netlify / Vercel / Cloudflare Pages**
   - 这些平台都能直接从 GitHub 仓库部署。
   - 同样只需要在配置里指定建站目录为仓库根目录即可。

3. **自建静态服务器**
   - 简单方法：
     ```sh
     # Python 3
     python -m http.server 8000
     # 或者使用 npm 包
     npx serve .
     ```
   - 文件放在任一 Web 服务器根目录（nginx、Apache）下即可。

## 评论功能说明
留言区使用 `localStorage` 存储，每个浏览器独立，适合演示和收集个人意见。若需要集中展示所有用户留言，请考虑接入后端数据库（例如 Firebase、Supabase、简单的 Express API 等）。

## 结构

- `index.html` – 全部页面内容
- `.github/workflows/pages.yml` –（可选）GitHub Pages 自动部署配置

---

© 2026 个人制作，欢迎分享与改进。