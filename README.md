# JSON Editor 中文版

[![Version](https://img.shields.io/npm/v/jsoneditor.svg)](https://www.npmjs.com/package/jsoneditor)
[![Downloads](https://img.shields.io/npm/dm/jsoneditor.svg)](https://www.npmjs.com/package/jsoneditor)
[![Maintenance](https://img.shields.io/maintenance/yes/2025.svg)](https://github.com/josdejong/jsoneditor/pulse)
[![License](https://img.shields.io/github/license/josdejong/jsoneditor.svg)](https://github.com/josdejong/jsoneditor/blob/master/LICENSE)
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2Fjosdejong%2Fjsoneditor.svg?type=shield)](https://app.fossa.io/projects/git%2Bgithub.com%2Fjosdejong%2Fjsoneditor?ref=badge_shield)

JSON Editor 是一个基于 Web 的工具，用于查看、编辑、格式化和验证 JSON。它提供多种编辑模式，包括树形编辑器、代码编辑器和纯文本编辑器。该编辑器可以作为组件集成到你自己的 Web 应用中，支持 CommonJS 模块、AMD 模块或普通 JavaScript 文件加载。

该库最初是作为流行的在线应用 https://jsoneditoronline.org 的核心组件开发的，此后已开源。

支持的浏览器：Chrome、Firefox、Safari、Edge。

<img alt="json editor" src="https://raw.github.com/josdejong/jsoneditor/master/misc/jsoneditor.png"> &nbsp; <img alt="code editor" src="https://raw.github.com/josdejong/jsoneditor/master/misc/codeeditor.png">

持续集成测试在 [GitHub Actions](https://github.com/josdejong/mathjs/actions) 上运行，并使用 [LambdaTest](https://www.lambdatest.com) 在所有主流浏览器上进行测试。

[![LambdaTest](https://raw.github.com/josdejong/mathjs/master/misc/lambdatest.svg)](https://www.lambdatest.com)

感谢 GitHub Actions 和 LambdaTest 对这个开源项目的慷慨支持！

## 继任者：svelte-jsoneditor

此库 [`jsoneditor`](https://github.com/josdejong/jsoneditor) 有一个继任者：[`svelte-jsoneditor`](https://github.com/josdejong/svelte-jsoneditor)。新编辑器并非一对一替代品，因此可能有理由继续使用 `jsoneditor`。
两者之间的主要区别[在此描述](https://github.com/josdejong/svelte-jsoneditor#differences-between-josdejongsvelte-jsoneditor-and-josdejongjsoneditor)。

## 功能特性

JSONEditor 提供多种模式，具有以下功能。

### 树形模式

- 更改、添加、移动、删除和复制字段和值。
- 对数组和对象排序。
- 使用 [JMESPath](http://jmespath.org/) 查询转换 JSON。
- 代码着色。
- 颜色选择器。
- 在树视图中搜索和高亮文本。
- 撤销和重做所有操作。
- JSON Schema 验证（由 [ajv](https://github.com/epoberezkin/ajv) 提供支持）。

### 代码模式

- 代码着色（由 [Ace](https://ace.c9.io) 提供支持）。
- 检查 JSON（由 [Ace](https://ace.c9.io) 提供支持）。
- 格式化和压缩 JSON。
- 修复 JSON。
- JSON Schema 验证（由 [ajv](https://github.com/epoberezkin/ajv) 提供支持）。

### 文本模式

- 格式化和压缩 JSON。
- 修复 JSON。
- JSON Schema 验证（由 [ajv](https://github.com/epoberezkin/ajv) 提供支持）。

### 预览模式

- 处理高达 500 MiB 的大型 JSON 文档。
- 使用 [JMESPath](http://jmespath.org/) 查询转换 JSON。
- 格式化和压缩 JSON。
- 修复 JSON。
- JSON Schema 验证（由 [ajv](https://github.com/epoberezkin/ajv) 提供支持）。

## 文档

- 文档：
  - [API](https://github.com/josdejong/jsoneditor/tree/master/docs/api.md)
  - [使用方法](https://github.com/josdejong/jsoneditor/tree/master/docs/usage.md)
  - [快捷键](https://github.com/josdejong/jsoneditor/tree/master/docs/shortcut_keys.md)
- [示例](https://github.com/josdejong/jsoneditor/tree/master/examples)
- [源代码](https://github.com/josdejong/jsoneditor)
- [更新历史](https://github.com/josdejong/jsoneditor/blob/master/HISTORY.md)


## 安装

使用 npm（推荐）：

    npm install jsoneditor

或者，你可以使用其他 JavaScript 包管理器如 https://yarnpkg.com/，或 CDN 如 https://cdnjs.com/ 或 https://www.jsdelivr.com/。

## 使用

> 注意：在以下示例中，你需要将 `jsoneditor/dist/jsoneditor.min.js` 和 `jsoneditor/dist/jsoneditor.min.css` 的 URL 更改为你下载库的位置，或填写你使用的 CDN 的 URL。

```html
<!DOCTYPE HTML>
<html lang="zh-CN">
<head>
    <!-- 使用 "code" 模式时，指定 charset utf-8 很重要 -->
    <meta charset="utf-8">

    <link href="jsoneditor/dist/jsoneditor.min.css" rel="stylesheet" type="text/css">
    <script src="jsoneditor/dist/jsoneditor.min.js"></script>
</head>
<body>
    <div id="jsoneditor" style="width: 400px; height: 400px;"></div>

    <script>
        // 创建编辑器
        const container = document.getElementById("jsoneditor")
        const options = {}
        const editor = new JSONEditor(container, options)

        // 设置 JSON
        const initialJson = {
            "数组": [1, 2, 3],
            "布尔值": true,
            "空值": null,
            "数字": 123,
            "对象": {"a": "b", "c": "d"},
            "字符串": "你好世界"
        }
        editor.set(initialJson)

        // 获取 JSON
        const updatedJson = editor.get()
    </script>
</body>
</html>
```


## 构建

JSON Editor 的代码位于 `./src` 文件夹中。要构建 jsoneditor：

- 安装依赖：

  ```
  npm install
  ```

- 构建 JSON Editor：

  ```
  npm run build
  ```

  这将在项目的 dist 目录中生成 `./jsoneditor.js`、`./jsoneditor.css` 及其压缩版本。

- 源文件更改时自动构建：

  ```
  npm start
  ```

  这将在每次更改时更新 dist 文件夹中的 `./jsoneditor.js` 和 `./jsoneditor.css`，但**不会**更新压缩版本，因为这是一个耗时的操作。


## 测试

运行单元测试：

```
npm test
```

运行代码检查（[JavaScript Standard Style](https://standardjs.com/)）：

```
npm run lint
```


## 部署

本项目配置了 GitHub Actions 自动部署。当推送以 `v` 开头的标签时，会自动构建并部署到服务器。

### 触发部署

```bash
# 创建并推送标签
git tag v10.4.3
git push origin v10.4.3
```

### 配置 Secrets

在 GitHub 仓库的 **Settings → Secrets and variables → Actions** 中添加以下 Secrets：

| Secret 名称 | 说明 | 示例 |
|------------|------|------|
| `DEPLOY_HOST` | 服务器 IP 或域名 | `192.168.1.100` 或 `example.com` |
| `DEPLOY_PORT` | SSH 端口 | `22` |
| `DEPLOY_USER` | SSH 用户名 | `root` 或 `deploy` |
| `DEPLOY_PASSWORD` | SSH 密码 | `your-password` |
| `NGINX_HTML_DIR` | 部署目标目录 | `/var/www/jsoneditor` |
| `GMAIL_USERNAME` | Gmail 邮箱（用于通知） | `your-email@gmail.com` |
| `GMAIL_PASSWORD` | Gmail 应用专用密码 | `xxxx xxxx xxxx xxxx` |
| `GMAIL_TO` | 接收通知的邮箱 | `notify@example.com` |

> **注意**：Gmail 需要使用[应用专用密码](https://support.google.com/accounts/answer/185833)，而非账户密码。

### Nginx 配置示例

```nginx
server {
    listen 80;
    server_name your-domain.com;

    root /var/www/jsoneditor;
    index index.html;

    location ~* \.(js|css|png|jpg|jpeg|gif|ico|svg|woff|woff2|ttf|eot|map)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }

    location ~* \.md$ {
        default_type text/plain;
        charset utf-8;
    }

    location / {
        try_files $uri $uri/ =404;
    }

    gzip on;
    gzip_types text/plain text/css application/json application/javascript text/xml application/xml;
    gzip_min_length 1000;
}
```


## 许可证

`jsoneditor` 以宽松的 [Apache 2.0 许可证](LICENSE.md) 开源发布。

**如果你在商业项目中使用 jsoneditor，我们有社会层面（非法律层面）的期望，希望你能帮助资助其维护。[从这里开始](https://github.com/sponsors/josdejong)。**
