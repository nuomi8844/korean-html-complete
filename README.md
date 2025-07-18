# 🌸 韩式个人链接页面 - 纯HTML版本
一个完全独立的韩式风格个人链接页面，采用纯HTML+CSS+JavaScript开发，无需任何框架依赖。
![韩式设计](https://img.shields.io/badge/设计风格-韩式粉色-ff69b4)
![纯HTML](https://img.shields.io/badge/技术-纯HTML-green)
![响应式](https://img.shields.io/badge/布局-响应式-blue)
![零依赖](https://img.shields.io/badge/依赖-零依赖-orange)
## ✨ 特色功能
- 🎨 **韩式美学设计** - 粉色渐变背景，现代化UI
- 📱 **完美响应式** - 384px容器，手机优先设计
- 📝 **文字格式控制** - 支持手动换行，不自动换行，全部居中
- 🖼️ **智能图片布局** - 主图+3小图+双相册展示
- 🔗 **多平台链接** - 支持Telegram、LINE、Instagram等
- ⚙️ **隐藏管理** - Ctrl+Shift+A进入管理模式
- 💾 **本地存储** - 修改内容自动保存
- 🚀 **一键部署** - 单文件，任意服务器可用
## 📐 精确设计规格
### 🎯 核心尺寸
- **容器宽度**: 384px (max-w-sm)
- **主图高度**: 192px
- **小图网格**: 3列 × 128px高度
- **相册布局**: 2列网格，3:4比例
- **链接卡片**: 80px高度，左图右文
### 🎨 设计系统
- **背景渐变**: 粉色系韩式渐变
- **圆角系统**: 8px/12px/16px/24px
- **字体大小**: 12px/14px/16px/20px/24px/30px
- **动画时长**: 0.3s/0.5s/0.6s/0.7s
## 🚀 快速开始
### 📥 下载使用
```bash
# 1. 克隆仓库
git clone https://github.com/nuomi8844/korean-html-complete.git
# 2. 进入目录
cd korean-html-complete
# 3. 直接打开
open index.html
```
### 🔧 本地预览
```bash
# Python 3
python -m http.server 8000
# Node.js
npx serve .
# 然后访问 http://localhost:8000
```
## 📝 内容修改指南
### 方法一：直接编辑HTML（推荐）
打开 `index.html`，找到 `siteConfig` 对象：
```javascript
const siteConfig = {
    // 🔐 管理密码
    adminPassword: "qwe5566@",
    // 🖼️ 主图和文字
    hero: {
        image: "您的图片链接",
        title: "您的标题",
        subtitle: "您的副标题\n支持换行",
        description: "您的描述\n支持多行\n完全按格式显示",
        clickUrl: "https://line.me/ti/p/您的LINE-ID"
    },
    // 📝 文字介绍区域
    textSections: {
        middle: {
            title: "🌟 您的标题",
            content: "您的内容\n支持换行\n居中显示"
        },
        bottom: {
            title: "💎 第二段标题",
            content: "第二段内容\n也支持换行"
        },
        final: {
            title: "🎉 最终标题",
            content: "最终内容\n感谢文字"
        }
    },
    // 🔗 第一组链接
    linksGroup1: [
        {
            title: "Telegram 联系",
            description: "即时聊天，快速响应",
            url: "https://t.me/您的用户名",
            image: "您的图片链接",
            icon: "telegram"
        },
        {
            title: "LINE 咨询",
            description: "专业客服，贴心服务",
            url: "https://line.me/ti/p/您的LINE-ID",
            image: "您的图片链接",
            icon: "line"
        }
    ],
    // 第二组链接、相册等配置...
}
```
### 方法二：在线管理面板
1. **显示管理按钮**: 按 `Ctrl+Shift+A`
2. **输入密码**: `qwe5566@` (可在HTML中修改)
3. **编辑内容**: 在弹出窗口中修改所有文字
4. **保存更改**: 自动保存到浏览器本地存储
## 🖼️ 图片替换指南
### 📏 推荐尺寸
- **主图**: 400×200px (2:1比例)
- **小图**: 150×150px (1:1比例)
- **相册图**: 300×400px (3:4比例)
- **链接图标**: 100×100px (1:1比例)
### 🔄 替换方法
1. **上传图片**到图床服务 (如Unsplash、imgur等)
2. **复制链接**替换配置中的图片URL
3. **刷新页面**查看效果
## 🎯 交互功能
### 🖱️ 点击跳转规则
- **主图和3小图** → 跳转到LINE
- **第一相册(6张图)** → 跳转到LINE
- **第二相册(6张图)** → 跳转到Telegram
- **链接卡片** → 跳转到对应URL
### ⌨️ 快捷键
- **Ctrl+Shift+A** → 显示管理按钮
- **Esc** → 关闭模态框
## 🌐 部署方法
### 🆓 免费部署选项
#### **GitHub Pages**
1. Fork本仓库
2. 在Settings → Pages中启用
3. 访问: `https://您的用户名.github.io/korean-html-complete/`
#### **Netlify**
1. 拖拽文件夹到Netlify
2. 自动部署完成
3. 获得免费域名
#### **Vercel**
1. 导入GitHub仓库
2. 一键部署
3. 全球CDN加速
### 🏢 私有服务器部署
#### **IIS (Windows)**
```xml
<!-- web.config -->
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <defaultDocument>
            <files>
                <add value="index.html" />
            </files>
        </defaultDocument>
    </system.webServer>
</configuration>
```
#### **Apache (Linux)**
```apache
# .htaccess
DirectoryIndex index.html
RewriteEngine On
```
#### **Nginx**
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /path/to/korean-html-complete;
    index index.html;
}
```
## 🎨 自定义主题
### 🌈 修改颜色主题
在HTML的 `<style>` 部分找到：
```css
/* 主背景渐变 */
background: linear-gradient(135deg, #fecaca 0%, #fde7f3 50%, #fecaca 100%);
/* 卡片背景色 */
background: rgba(251, 207, 232, 0.8);
/* 边框颜色 */
border: 1px solid #fbb6ce;
```
修改这些颜色代码即可改变主题！
### 📐 调整布局
```css
/* 容器宽度 */
max-width: 384px; /* 改为您想要的宽度 */
/* 主图高度 */
height: 192px; /* 改为您想要的高度 */
/* 相册间距 */
gap: 16px; /* 改为您想要的间距 */
```
## 📱 移动端优化
### 📞 移动端特色
- **一键拨打**: 支持 `tel:` 链接
- **应用跳转**: 支持社交APP深度链接
- **手势友好**: 适合手指点击的按钮大小
- **加载优化**: 图片懒加载，快速响应
### 🔗 深度链接示例
```javascript
// Telegram
"tg://resolve?domain=您的用户名"
// LINE
"line://ti/p/您的LINE-ID"
// WhatsApp
"https://wa.me/您的电话号码"
// 微信 (需要特殊处理)
"weixin://dl/chat"
```
## 🛠️ 高级功能
### 📊 访问统计
可以集成Google Analytics或其他统计工具：
```html
<!-- 在</head>前添加 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_MEASUREMENT_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'GA_MEASUREMENT_ID');
</script>
```
### 🔒 密码管理
修改管理密码：
```javascript
// 在siteConfig中修改
adminPassword: "您的新密码",
```
### 💾 数据备份
导出配置：
```javascript
// 在浏览器控制台运行
console.log(JSON.stringify(localStorage.getItem('siteConfig')));
```
## 🔧 常见问题
### ❓ 图片不显示
- 检查图片链接是否有效
- 确认图片支持HTTPS访问
- 使用Unsplash等稳定图床
### ❓ 手机端样式异常
- 确保包含viewport meta标签
- 检查CSS媒体查询
- 测试不同设备尺寸
### ❓ 管理面板无法打开
- 确认按下Ctrl+Shift+A
- 检查浏览器控制台错误
- 尝试刷新页面重试
### ❓ 本地存储失效
- 使用HTTP服务器预览
- 检查浏览器隐私设置
- 清除浏览器缓存重试
## 📞 技术支持
### 🔗 相关链接
- **在线演示**: [GitHub Pages](https://nuomi8844.github.io/korean-html-complete/)
- **问题反馈**: [GitHub Issues](https://github.com/nuomi8844/korean-html-complete/issues)
- **功能建议**: 通过Issues提交
### 💡 贡献指南
欢迎提交Pull Request来改进项目：
1. Fork仓库
2. 创建特性分支
3. 提交修改
4. 发起Pull Request
## 📄 开源协议
本项目采用 MIT 协议开源，您可以自由使用、修改和分发。
---
## 🎉 享受您的韩式链接页面！
这个纯HTML版本让您完全掌控网站内容，无需学习复杂的框架，用记事本就能轻松定制。希望它能为您带来更多的连接和机会！
**⭐ 如果这个项目对您有帮助，请给个Star支持一下！**