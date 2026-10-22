# 部署到网上保姆级图文步骤（最终版）

目标：把 IFC 查看器发布到网上，任何人通过网址即可访问。
架构：
- **网页本身** → GitHub Pages（免费，无需服务器）
- **文件存储** → Supabase（免费，无需绑卡）——用户上传的 IFC 文件存这里，生成链接分享

**当前进度：✅ Supabase 云端存储已配置完成（账号已注册、存储桶已建、权限已开、网址密钥已填进网页配置）。**
剩下只需：**上传 GitHub → 开启 Pages**（约 5 分钟）。

---

## 剩余步骤：上传 GitHub 并开启 Pages

### 第 1 步：新建 GitHub 仓库
1. 打开 https://github.com ，登录您的账号（如还未注册：https://github.com/signup 免费注册）
2. 右上角 **「+」→「New repository」**
3. **Repository name** 填：`ifc-viewer`
4. 选择 **Public**（公开）
5. **不要**勾选 "Add a README file"
6. 点绿色按钮 **「Create repository」**

### 第 2 步：上传网站文件
1. 仓库页面会有一个链接 **"uploading an existing file"**，点它
2. 打开部署包文件夹 `IFC-Viewer部署包-GitHub`
3. 把里面**所有内容**（index.html、assets 文件夹、web-ifc.wasm、使用说明.md、README.md）**直接拖进**浏览器上传区域
4. 点 **「Commit changes」**

### 第 3 步：开启网页访问
1. 仓库顶部标签 **「Settings」→ 左侧「Pages」**
2. **Source** 选 **"Deploy from a branch"**
3. **Branch** 选 **main**，右边选 **/(root)**，点 **「Save」**
4. 等 **1～3 分钟**，Settings→Pages 页面顶部出现：
   **"Your site is live at https://你的用户名.github.io/ifc-viewer/"**

### 第 4 步：测试上线
1. 浏览器打开这个网址 → 显示**主页**（上传界面）
2. 点「选择 IFC 文件」或把 .ifc 文件拖进页面 → 文件上传到云端
3. 上传成功 → 显示**链接** → 复制发给任何人 → 对方打开即可查看模型（无需登录、无需安装）

---

## 使用效果

- 打开网址 → **主页**（上传界面）
- 上传 IFC → 显示**链接**（永久有效，云端保存）
- 把链接发给同事/客户 → 浏览器打开即进入**查看器**查看模型
- 免费额度：Supabase 存储 1GB、GitHub 不限量（此使用量远用不完）

## 常见问题

| 问题 | 解决方法 |
| ---- | ---- |
| 打开网址 404/空白 | 等 2-3 分钟刷新；确认文件都传在仓库**根目录**（不要放进子文件夹） |
| 上传失败 | 确认上传的模型小于 50MB（Supabase 免费版限制）；刷新重试 |
| 想删除已传文件 | 登录 supabase.com → 项目 → Storage → ifc-files 桶 → 删除文件 |
| 国内访问 GitHub 慢 | 属正常现象；如需更稳定可后续迁移国内云（联系豆包协助） |
| 以后更新软件 | 让豆包重新生成部署包 → GitHub 仓库删旧传新 → 等生效 |

## 备份信息（重要，请保存）

- **Supabase 项目网址**：https://jtibpyjmqqxswqfeszkn.supabase.co
- **Supabase 公开密钥**（可公开，网页配置用）：sb_publishable_3i_nEwA4MoYWEBJLM89HRA_PGurRMxv
- **Supabase 数据库密码**（后台管理用，勿外泄）：jOhDCwqYDEoLZSkC
- 以上已自动填进 `index.html`，您无需手动修改任何文件
