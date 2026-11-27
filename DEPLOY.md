# 发布到 GitHub Pages

站点域名：`marry.chenrx.top`。

## 发布内容

- `christmas-stardust.html`：星尘版，部署时自动成为 `index.html`。
- `Last Christmas-Taylor+Swift.mp3`：页面引用的音乐文件。
- `.github/workflows/deploy-pages.yml`：推送到 `main` 后自动部署。

工作流只发布这两个站点文件。

## 首次配置

1. 使用仓库 `https://github.com/ABCD-crx/merry_christmas.git`，默认分支使用 `main`。
2. 将本项目推送到该仓库；如果从部署压缩包开始，先解压并进入包含 `.github` 和 `christmas-stardust.html` 的目录。
3. 在仓库 **Settings → Pages → Build and deployment → Source** 选择 **GitHub Actions**。
4. 如果首次工作流在启用 Pages 前失败，在 **Actions** 中重新运行工作流。
5. 在该仓库 **Settings → Pages → Custom domain** 中保存 `marry.chenrx.top`。
6. 登录 Cloudflare，打开 **chenrx.top → DNS → Records**，添加以下记录：

| 配置项 | 值 |
| --- | --- |
| Type | CNAME |
| Name | marry |
| Target | abcd-crx.github.io |
| Proxy status | DNS only（灰色云朵） |
| TTL | Auto |

7. 等待 DNS 校验与 HTTPS 证书签发后，在 GitHub Pages 设置中勾选 **Enforce HTTPS**。

原博客的 DNS 和仓库设置保留即可。自定义 Actions 发布工作流不需要仓库内的 CNAME 文件。

## 更新

修改 `christmas-stardust.html` 后推送到 `main`，Actions 会重新发布。
音乐由访客点击页面上的音乐按钮后播放。

## 参考

- https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages
- https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site
