`src` 分支是整个博客的源文件，每次有新博客或者旧博客修改都应在 `src` 分支进行操作。<br/>
`master` 分支是部署分支，使用 `github pages` 进行预览阅读。

新博客或旧博客修改步骤：

1. `hexo server|s` 本地预览效果；

2. 确认无误后依次执行 `hexo clean`，`hexo generate|g`，`hexo deploy|d`；

```bash
// Remove generated files and cache.
hexo clean

// Deploy your website.
hexo deploy

// Generate static files.
hexo generate

// Start the server.
hexo server 
```

