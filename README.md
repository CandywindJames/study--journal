# 研途 · 每日复习手账

React + TypeScript 静态网站，Supabase Auth / PostgreSQL / Storage 保存个人数据。

## 首次上线

1. GitHub 仓库 Settings → Pages → Source 选择 **Deploy from a branch**。
2. Branch 选择 **main**，目录选择 **/docs**，点击 Save。
3. 等待 GitHub Pages 完成部署，网站地址为 https://candywindjames.github.io/study--journal/ 。
4. Supabase 项目 `study-journal` → Authentication → URL Configuration：Site URL 设置为上述网站地址，Redirect URLs 也添加同一地址。
5. 打开网站注册独立账号。默认邮件服务只向 Supabase 组织成员邮箱发送邮件，所以首次使用请使用你的 Supabase 账号邮箱；其他邮箱需要自定义 SMTP。通过确认邮件后登录。不要在聊天或代码里填写密码。

## 功能

- 按日期添加、修改、完成和删除任务。
- 数学一、英语一、政治、408，2009—2026 年真题成绩，多轮练习、备注和趋势。
- 模拟卷上传、下载、删除与记分；每份文件最多 20 MB。
- 切回网页和每 30 秒自动刷新云端记录。
- 导出 JSON 文字记录；试卷文件需另外下载。导出备份不包含密码或登录凭证。

## 数据与权限

云端项目：`xacnqksvcaaphpfhyuwd`。
表：`study_tasks`、`study_scores`、`study_files`。私人存储桶：`study-papers`。
所有表启用 RLS，按 `auth.uid() = user_id` 隔离；文件路径以用户 ID 为首层目录。
浏览器代码中只有可公开的 publishable key，没有 service_role 或管理员密钥。
旧 ChatGPT Sites 数据未自动迁移到本网站。

## 修改与构建

需要 Node.js 22.13+。

```sh
npm ci
npm run dev
npm run build
```

`docs/` 是构建好的静态网站。修改 `src/` 后执行构建，将源码和 `docs/` 一起提交到 main。GitHub Pages 会重新发布。

## 当前验证范围

TypeScript 检查和生产构建通过，数据库权限及 Supabase security advisors 已检查。
尚未完成真实用户注册、登录和跨设备端到端验证。
