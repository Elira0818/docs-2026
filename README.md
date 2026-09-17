# 文档库

把 Word / Excel / PDF 转成网页，方便在 GitHub 上直接看内容。

## 目录结构

```
index.html            文件列表首页
pages/*.html          每个文件对应的网页版正文
files/*               原始文件（可下载）
assets/*              从 Word 里抽出来的图片
manifest.json         文件索引（自动生成，别手改）
```

## 推送到 GitHub

仓库已经 `git init` 好了，就差远端地址和推送。

**1. 在 GitHub 新建一个空仓库**（建议私有则不要勾选任何初始化选项）

**2. 在本机配置身份**（只需一次，邮箱要用 GitHub 注册邮箱，否则提交不显示在你的贡献图上）

```bash
cd docs-repo
git config user.name  "你的名字"
git config user.email "你的GitHub邮箱"
```

**3. 加远端并推送**

```bash
git remote add origin https://github.com/<用户名>/<仓库名>.git
git branch -M main
git push -u origin main
```

如果提示输入密码：GitHub 早已不支持账号密码推送，需要在
`GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)`
生成一个勾选 `repo` 的 token，用 token 当密码粘贴。

## 打开网页版

推送完成后，在仓库 **Settings → Pages** 里把 Source 设为 `Deploy from a branch`、分支 `main`、目录 `/ (root)`，保存后得到形如下面的地址：

```
https://<用户名>.github.io/<仓库名>/index.html
```

> ⚠️ 免费 GitHub 账号的**私有仓库无法启用 Pages**。若仓库是私有的，Pages 选项会不可用；
> 需要升级到 GitHub Pro，或把仓库改成 Public。
>
> 私有仓库下能用的替代方式：登录 GitHub 后打开
> `https://github.com/<用户名>/<仓库名>/blob/main/pages/xxx.html`，点右上角的 Raw 或直接下载 HTML 到本地用浏览器打开。

## 继续添加文件

运行 `start-uploader.bat`（或 `python server.py`），浏览器会打开上传页，
点「＋ 继续添加文件」把新文件拖进去，页面会自动重新生成并提交，
最后点「推送到 GitHub」同步。
