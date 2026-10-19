# 我的博客

使用 [Fuwari](https://github.com/saicaca/fuwari) 和 Astro，部署在 GitHub Pages。

- 博客：https://dumachen.github.io/
- 仓库：https://github.com/DuMaChen/DuMaChen.github.io

## 本地编辑

推荐 Node.js 24 LTS，pnpm 9.14.4。

```sh
pnpm install --frozen-lockfile
pnpm dev
```

打开 http://localhost:4321/ 。站点信息、头像和主题配色在 src/config.ts；关于页面在 src/content/spec/about.md。

## 新建文章

```sh
pnpm new-post my-new-post
```

编辑 src/content/posts/ 下的 Markdown，补充 title、published 等信息，draft 设为 false。

## 发布

在此项目目录执行：

```sh
pnpm check && pnpm build
git add .
git commit -m "Publish new post"
git push origin main
```

GitHub Actions 会自动检查、构建并发布，包含 Pagefind 搜索索引。
推送后在仓库的 Actions 页面查看执行结果；成功后刷新博客即可。

不需要手动上传 dist/，也不需要 SSH 登录旧服务器。
在 GitHub 网页上直接编辑并提交文章，也会触发相同的自动部署。

## 域名

当前使用 GitHub 提供的 HTTPS 地址。若以后绑定自己的域名，需要配置 Pages 自定义域名、DNS，并修改 astro.config.mjs 的 site。

## 许可

主题代码遵循仓库中的 MIT LICENSE；文章许可由 src/config.ts 的 licenseConfig 控制。
