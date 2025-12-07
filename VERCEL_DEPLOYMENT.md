# Vercel 部署指南

## 问题：部署后没有"写祝福"和"抽祝福"按钮

这是因为 Vercel 部署时没有配置 Waline 环境变量。按钮的显示由 `isWalineConfigured()` 函数控制，该函数检查 `VITE_WALINE_SERVER_URL` 是否已配置。

## 解决方案

### 步骤 1：在 Vercel 项目中配置环境变量

1. 登录 [Vercel Dashboard](https://vercel.com/dashboard)
2. 选择你的项目
3. 进入 **Settings** → **Environment Variables**
4. 添加以下环境变量：

#### 必需的环境变量

| 变量名 | 值 | 说明 |
|--------|-----|------|
| `VITE_WALINE_SERVER_URL` | `https://your-waline-server.com` | 你的 Waline 服务器地址 |

#### 可选的环境变量

| 变量名 | 默认值 | 说明 |
|--------|--------|------|
| `VITE_ENABLE_GESTURE_CONTROL` | `false` | 是否启用手势控制 |
| `VITE_ENABLE_COMMENT_REPLY` | `false` | 是否启用评论回复 |
| `VITE_SHOW_OTHERS_BLESSINGS` | `true` | 是否显示他人祝福 |
| `VITE_TREE_ROTATION_SPEED` | `1.0` | 圣诞树旋转速度 |
| `VITE_SHOW_DEBUG_BUTTON` | `false` | 是否显示调试按钮 |
| `VITE_SHOW_SENDER_EMAIL` | `false` | 是否显示发送者邮箱 |

**密度配置**（影响性能，建议使用默认值）：
- `VITE_FOLIAGE_DENSITY` - 树叶密度（默认 20000）
- `VITE_PHOTO_DENSITY` - 照片密度（默认 160）
- `VITE_ENVELOPE_DENSITY` - 信封密度（默认 50）
- `VITE_ELEMENT_DENSITY` - 圣诞元素密度（默认 180）
- `VITE_LIGHT_DENSITY` - 彩灯密度（默认 200）

### 步骤 2：重新部署

配置环境变量后，需要触发重新部署：

**方法 1：通过 Vercel Dashboard**
1. 进入项目的 **Deployments** 页面
2. 点击最新部署旁的 ⋯ 按钮
3. 选择 **Redeploy**

**方法 2：推送新提交**
```bash
git commit --allow-empty -m "Trigger rebuild"
git push
```

### 步骤 3：验证部署

1. 等待部署完成
2. 访问你的网站
3. 检查是否显示以下按钮：
   - 💌 写祝福
   - 🎄 抽祝福
   - 👤 我的

## 快速检查清单

- [ ] 已在 Vercel 配置 `VITE_WALINE_SERVER_URL` 环境变量
- [ ] Waline 服务器地址正确且可访问
- [ ] 已触发重新部署
- [ ] 按钮已正常显示
- [ ] 可以正常写评论和抽取评论

## 调试技巧

### 1. 启用调试模式

临时设置环境变量：
```
VITE_SHOW_DEBUG_BUTTON=true
```

重新部署后，点击"显示调试"按钮查看配置信息。

### 2. 检查浏览器控制台

打开浏览器开发者工具（F12），查看控制台输出：
- 应该看到 `walineEnabled: true`
- 检查是否有 Waline 相关的错误信息

### 3. 验证环境变量

在 Vercel Dashboard 中：
1. Settings → Environment Variables
2. 确认变量在正确的环境中（Production/Preview/Development）
3. 确认变量值没有多余的空格

## 常见问题

### Q: 配置了环境变量，但按钮还是不显示？

**A:** 确保：
1. 环境变量名称完全正确（区分大小写）
2. 已经重新部署（环境变量更改不会自动触发部署）
3. Waline 服务器地址不是默认的示例地址 `https://your-waline-server.example.com`

### Q: 如何搭建 Waline 服务器？

**A:** 参考 Waline 官方文档：
- [Waline 快速开始](https://waline.js.org/guide/get-started/)
- [Vercel 部署 Waline](https://waline.js.org/guide/deploy/vercel.html)

### Q: 可以使用其他评论系统吗？

**A:** 目前项目只支持 Waline。如需支持其他评论系统，需要修改代码。

## 需要帮助？

如果按照以上步骤操作后仍有问题，请检查：
1. Waline 服务器是否正常运行
2. 浏览器控制台是否有错误信息
3. 网络连接是否正常

---

**提示**：本地开发时，创建 `.env` 文件（从 `.env.example` 复制）并配置相同的环境变量。
