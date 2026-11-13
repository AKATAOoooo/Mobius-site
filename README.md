# Möbius 下载页

一个纯静态页（单文件 HTML + 图标），给 GitHub Pages 用。
不需要构建工具、不需要 npm，改完直接推。

## 文件

- `index.html` —— 页面（内联 CSS，无 JS 依赖）
- `assets/icon.png` —— App 图标（512×512，从 AppIcon.icns 导出）
- `README.md` —— 本文件

## 发布到 GitHub Pages（一次性设置）

### 1. 建仓库

在 GitHub 新建 **公开** 仓库，名字建议 `mobius-site`，**不要**勾 README / .gitignore。

### 2. 推文件

```bash
cd ~/AI应用/Mobius下载页
git init -b main
git add -A && git commit -m "init: 下载页"
git remote add origin git@github.com:<你的用户名>/mobius-site.git
git push -u origin main
```

### 3. 传安装包（Releases）

仓库页 → **Releases** → **Draft a new release**：

- Tag：`v1.16.5`
- 标题：`Möbius 1.16.5`
- 附件：把 `Mobius-1.16.5.dmg` **改名成 `Mobius-latest.dmg`** 再拖进去
  （页面上的下载按钮固定指向这个名字，以后换版本也只需替换同名附件）
- 发布

### 4. 开 Pages

仓库 → **Settings** → **Pages**：

- Source：`Deploy from a branch`
- Branch：`main` / `/ (root)`
- Save

一两分钟后访问 `https://<你的用户名>.github.io/mobius-site/`。

## 以后更新版本

1. 改 `index.html` 里的三处版本信息（搜索 `v1.16.5`，约 2 处 + meta 里的 38 MB）；
2. 新建一个 Release，附件仍然叫 `Mobius-latest.dmg`；
3. 页面上的「下载 macOS 版」会自动指向最新 Release（因为用的是 `releases/latest/download/Mobius-latest.dmg`）。

## 换仓库名要改哪里

页面里有 3 处链接写死了 `AKATAOoooo/mobius-site`：

```bash
grep -n "mobius-site" index.html
```

改完再推即可。

## 本地预览

```bash
cd ~/AI应用/Mobius下载页 && python3 -m http.server 8000
# 打开 http://127.0.0.1:8000/
```
