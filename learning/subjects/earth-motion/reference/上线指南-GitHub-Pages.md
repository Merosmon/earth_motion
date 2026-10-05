# 上线指南：把「地球运动」放到 GitHub Pages

署名：**AmaAstro**　·　本文写给「第一次做网站」的人，每一步都可照点。

---

## 上线后你会得到什么

```
https://amaastro.github.io/earth-motion/          ← 课程首页
https://amaastro.github.io/earth-motion/about.html ← 关于本站
```

- **免费**，不用买服务器、不用买域名
- **长期存在**，只要你不删仓库
- 国内访问**能开但可能时快时慢**（这个后面有说明和补救办法）

---

## 第 0 步：先注册账号（约 5 分钟）

打开 <https://github.com/signup>

| 要填的 | 填什么 | 注意 |
|---|---|---|
| 邮箱 | 你常用的 | 要能收验证邮件 |
| 密码 | 自己定 | 至少 8 位，含数字或小写字母 |
| **用户名** | **`AmaAstro`** | ★ **这一步最关键**——用户名决定你的网址 |
| 验证 | 按提示拼图 / 输验证码 | |

**为什么用户名要用 `AmaAstro`**：网址会是 `amaastro.github.io`，和你的署名一致。
如果这个名字已被占用，注册页会当场提示，那就换一个（比如 `AmaAstro-cn`、`Ama-Astro`），
**但要记住你最终用的名字**，后面的网址都按它来。

> **大小写说明**：GitHub 的用户名不区分大小写，注册成 `amaastro` 和 `AmaAstro` 是同一个账号，
> 网址统一显示为小写。

---

## 第 1 步：建一个仓库（约 1 分钟）

1. 登录后点右上角 **`+`** → **New repository**
2. 填两处：

| 项 | 填什么 |
|---|---|
| **Repository name** | **`earth-motion`** |
| 可见性 | 选 **Public**（公开） |

> **为什么必须选 Public**：GitHub Pages 的免费版只对公开仓库提供站点服务。私有仓库要付费。

3. 下面的 "Add a README file" 之类**都不用勾**
4. 点 **Create repository**

---

## 第 2 步：上传网站文件（约 5 分钟）

1. 新建好的仓库页面里，点 **Add file** → **Upload files**
2. 把桌面上 **`地球运动-网站.zip` 先解压**，得到三样东西：

```
index.html
.nojekyll           ← 注意：这是隐藏文件（点号开头）
.learning/          ← 这个文件夹里装着所有课程内容与资源
```

3. **把这三样一起拖进上传区**
   （可以直接拖文件夹，GitHub 会自动展开里面所有文件）

> ⚠️ **三个最容易犯的错，请逐个核对**：
>
> **① 不要只拖 `lessons` 文件夹。**
> 课件用相对路径引用 `../../assets/` 里的样式与公式字体，必须保持
> `index.html` + `.learning/` 这层结构一起传，页面才显示得对。
>
> **② `.nojekyll` 必须传上去——这个文件决定成败。**
> GitHub Pages 默认会用 Jekyll 引擎构建站点，而 **Jekyll 会忽略以 `_` 开头的文件与目录**。
> 你的共享资源正好放在 `.learning/` 里（下划线开头的文件夹），
> **不传 `.nojekyll`，整个 `.learning/` 都不会被发布**——后果是所有课件丢掉样式、
> 公式变成一堆乱码般的 TeX 源码。
>
> **③ 但 `.nojekyll` 是"隐藏文件"（点号开头），Windows 资源管理器默认不显示它**，
> 拖拽上传时很可能被跳过。两个办法，选一个：
>
> - **办法 A（推荐，最稳）**：传完后在仓库页点 **Add file → Create new file**，
>   文件名填 **`.nojekyll`**，内容**留空**，直接 **Commit changes**。
>   这样一定成功，也不怕拖拽漏掉。
> - **办法 B**：先在资源管理器的「查看」选项卡里勾上 **「隐藏的项目」**，
>   确认能看到 `.nojekyll`，再把它拖进上传区。

4. 上传完，下面填一句说明，比如 `第一次上线：第 1–4 课`
5. 点 **Commit changes**

> **小提示**：如果 `.learning` 里文件较多、网页上传卡住，就分几次传
> （GitHub 单次最多 100 个文件）。

---

## 第 3 步：打开 Pages（约 2 分钟）

1. 仓库页面上方点 **Settings**（如果没看到，点 `...` 展开菜单）
2. 左侧栏往下找，点 **Pages**
3. 在 **Build and deployment** 那里设置：

| 项 | 选什么 |
|---|---|
| **Source** | **Deploy from a branch** |
| **Branch** | **`main`**，右边目录选 **`/ (root)`** |
| 然后 | 点 **Save** |

> **注意**：GitHub 近年在改这套流程，有的账号默认显示的是 **GitHub Actions** 方式。
> 如果你想省事，**就选「Deploy from a branch」**（分支方式），一步到位。
> 若界面里找不到分支选项，就保持默认的 Actions 方式，它也能发布，只是首次会跑一次构建。

---

## 第 4 步：等它构建，然后打开网址

回到 **Settings → Pages**，页面顶部会出现一行提示（可能写着）：

```
Your site is live at https://amaastro.github.io/earth-motion/
```

**注意官方给的时间口径**：**改动最多需要 10 分钟**才会发布出来。
所以第一次如果打开是 404，**别急，等几分钟再刷新**——这不是你操作错了。

**要检查的四件事**：

1. 课程首页能打开，能看到路线图
2. 点进**第 1 课**，**图、公式、题目都在**（如果公式变成一堆 `\frac` 之类的源码、页面没有样式，
   说明 `.nojekyll` 没传上去，回第 2 步看「办法 A」）
3. 右上角点 **「关于本站」**，About 页能开
4. 手机上也打开一次，确认窄屏排版正常

---

## 以后更新怎么办（每次加新课）

1. 电脑上让我（或你自己）跑一次重建，得到新的 `地球运动-网站.zip`
2. 解压，**把改动过的文件传到同一个仓库**（GitHub 会提示覆盖）
3. 等 1 分钟，网址自动更新——**网址永远不变**

---

## 关于「国内访问有时慢」

**这是 GitHub Pages 的固有情况，不是你操作错了。**

- 打开慢或偶尔打不开 → **刷新一两次**通常就好
- 想彻底解决，有两条路（都需要额外成本，现在**不用急**）：

| 办法 | 成本 | 说明 |
|---|---|---|
| 绑自己的域名 | 几十元/年 | 网址更正式（`你的名字.com`），但要实名认证；**速度和稳定性不会因此变快** |
| 换国内托管 | 需要实名+可能绑卡 | 腾讯云 COS / 阿里云 OSS，国内快，但有免费额度限制 |

**我的建议**：**先用 `amaastro.github.io` 跑起来**。等站点内容够多了、确实要时常给别人看，
再考虑域名或换托管——**那时候换，网址可以跟着搬，前面的工作不浪费**。

---

## 遇到问题怎么办

| 现象 | 原因 | 怎么办 |
|---|---|---|
| 打开是 404 | Pages 还没构建完（**官方口径：最多 10 分钟**） | 等几分钟再刷新；确认 Branch 选了 `main` 且目录是 `(root)` |
| **页面能开但没有样式，公式变成一堆源码** | **`.nojekyll` 没传上去**（Jekyll 把 `.learning/` 整个忽略了） | 回第 2 步「办法 A」：用 Create new file 建一个空 `.nojekyll` |
| 点课件是 404 | `lessons` 传丢了 | 检查 `.learning/subjects/earth-motion/lessons/` 下四个 html 是否都在 |
| About 页打不开 | `about.html` 没传 | 它应在 `.learning/subjects/earth-motion/about.html` |
| 图片/字体在某些网络下加载慢 | GitHub Pages 国内速度波动 | 刷新即可，或按上面的「国内访问」一节处理 |

---

## 一句话总结流程

```
注册（用户名 AmaAstro）
  → 建公开仓库 earth-motion
  → 上传 index.html + .nojekyll + .learning/
  → Settings → Pages → Deploy from a branch → main / (root) → Save
  → 等最多 10 分钟 → 打开 https://amaastro.github.io/earth-motion/
```

**上线后自检这一条最关键**：随便点进一课，**看公式有没有正常排版**。
公式排好了，说明 `.nojekyll` 与 `.learning/` 都对；公式变成源码，就是 `.nojekyll` 没传。

---

## 附：这份指南是哪来的

- **GitHub 官方文档**（用户界面里的步骤、Public 仓库的要求、10 分钟发布上限、
  以及 `.nojekyll` 的作用）：<https://docs.github.com/zh/pages/getting-started-with-github-pages/creating-a-github-pages-site>
- 其余是你这个站点的具体结构带来的注意事项（`.learning/` 以下划线开头、
  课件用相对路径引用共享资源），由站点的构建脚本 `app/build_site.py` 保证。
