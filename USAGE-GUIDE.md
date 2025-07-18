# 📖 使用指南 - 韩式链接页面

详细介绍如何修改和定制您的韩式链接页面的每一个部分。

## 🎯 快速修改指南

### 1. 基本信息修改

打开 `index.html` 文件，找到 `siteConfig` 对象（约第400行），按以下方式修改：

#### 🔐 修改管理密码
```javascript
const siteConfig = {
    adminPassword: "您的新密码",  // 默认: qwe5566@
    // ...
}
```

#### 🖼️ 修改主图和标题
```javascript
hero: {
    image: "https://您的图片链接.jpg",
    title: "您的主标题",
    subtitle: "您的副标题\n可以换行\n支持多行",
    description: "您的描述文字\n也可以多行\n完全按您输入的格式显示",
    clickUrl: "https://line.me/ti/p/您的LINE-ID"  // 点击主图跳转的链接
},
```

**文字格式说明**:
- 使用 `\n` 来换行
- 所有文字会自动居中显示
- 不会自动换行，完全按您的格式显示

### 2. 修改文字介绍区域

```javascript
textSections: {
    // 第一段文字（在主图下方）
    middle: {
        title: "🌟 您的标题",
        content: "您的内容\n支持换行\n会完全按格式显示"
    },

    // 第二段文字（在第一相册下方）
    bottom: {
        title: "💎 第二段标题",
        content: "第二段内容\n也可以多行"
    },

    // 最终文字（在页面底部）
    final: {
        title: "🎉 结尾标题",
        content: "感谢访问\n期待与您联系"
    }
},
```

### 3. 修改链接卡片

#### 第一组链接（在第一段文字下方）
```javascript
linksGroup1: [
    {
        title: "Telegram 联系",
        description: "即时聊天，快速响应",
        url: "https://t.me/您的用户名",
        image: "https://您的图片链接.jpg",
        icon: "telegram"  // 可选: telegram, line, instagram, wechat
    },
    {
        title: "LINE 咨询",
        description: "专业客服，贴心服务",
        url: "https://line.me/ti/p/您的LINE-ID",
        image: "https://您的图片链接.jpg",
        icon: "line"
    }
],
```

#### 第二组链接（在第二相册下方）
```javascript
linksGroup2: [
    {
        title: "Instagram",
        description: "精彩内容，每日更新",
        url: "https://instagram.com/您的用户名",
        image: "https://您的图片链接.jpg",
        icon: "instagram"
    },
    {
        title: "微信联系",
        description: "添加微信，获取更多信息",
        url: "#",  // 微信通常设为#，因为无法直接跳转
        image: "https://您的图片链接.jpg",
        icon: "wechat"
    }
]
```

### 4. 修改相册图片

#### 第一相册（点击跳转到LINE）
```javascript
gallery1: {
    title: "📸 精选作品展示",
    clickUrl: "https://line.me/ti/p/您的LINE-ID",  // 所有图片点击跳转的链接
    images: [
        {
            src: "https://您的图片1.jpg",
            title: "图片标题1",
            description: "图片描述1\n可以换行"
        },
        {
            src: "https://您的图片2.jpg",
            title: "图片标题2",
            description: "图片描述2"
        },
        // ... 继续添加，最多建议6-10张
    ]
},
```

#### 第二相册（点击跳转到Telegram）
```javascript
gallery2: {
    title: "✨ 更多精彩内容",
    clickUrl: "https://t.me/您的用户名",  // 所有图片点击跳转的链接
    images: [
        {
            src: "https://您的图片1.jpg",
            title: "内容标题1",
            description: "内容描述1\n可以换行"
        },
        // ... 继续添加
    ]
}
```

### 5. 修改小图网格

```javascript
smallGallery: [
    {
        image: "https://小图1.jpg",
        clickUrl: "https://line.me/ti/p/您的LINE-ID"
    },
    {
        image: "https://小图2.jpg",
        clickUrl: "https://line.me/ti/p/您的LINE-ID"
    },
    {
        image: "https://小图3.jpg",
        clickUrl: "https://line.me/ti/p/您的LINE-ID"
    }
],
```

### 6. 修改底部文字

```javascript
bottomText: {
    text1: "您的第一行文字",
    text2: "您的第二行文字"
},
```

## 🖼️ 图片使用指南

### 📏 推荐尺寸

| 图片类型 | 推荐尺寸 | 比例 | 用途 |
|---------|---------|------|------|
| 主图 | 400×200px | 2:1 | 页面顶部大图 |
| 小图 | 150×150px | 1:1 | 主图下方3张小图 |
| 相册图 | 300×400px | 3:4 | 相册展示图片 |
| 链接图标 | 100×100px | 1:1 | 链接卡片左侧图片 |

### 🌐 图片来源建议

#### 免费图片网站
- **Unsplash**: https://unsplash.com (高质量免费图片)
- **Pixabay**: https://pixabay.com (免费商用图片)
- **Pexels**: https://pexels.com (专业摄影图片)

#### 图床服务
- **imgur**: https://imgur.com (免费图床)
- **PostImage**: https://postimg.cc (稳定图床)
- **SM.MS**: https://sm.ms (国内访问快)

#### 使用方法
1. 选择图片并上传到图床
2. 复制图片的直链地址
3. 替换配置中的图片URL
4. 刷新页面查看效果

## 🎨 样式自定义

### 🌈 修改颜色主题

在HTML文件的 `<style>` 部分找到相应代码并修改：

#### 背景渐变色
```css
/* 找到这行并修改颜色 */
background: linear-gradient(135deg, #fecaca 0%, #fde7f3 50%, #fecaca 100%);

/* 例如改为蓝色主题 */
background: linear-gradient(135deg, #dbeafe 0%, #e0e7ff 50%, #dbeafe 100%);
```

#### 卡片背景色
```css
/* 主卡片背景 */
background: rgba(251, 207, 232, 0.8);  /* 粉色 */

/* 改为蓝色 */
background: rgba(219, 234, 254, 0.8);
```

#### 边框颜色
```css
/* 卡片边框 */
border: 1px solid #fbb6ce;  /* 粉色边框 */

/* 改为蓝色边框 */
border: 1px solid #93c5fd;
```

### 📐 修改布局尺寸

#### 容器宽度
```css
/* 找到 .container 样式 */
.container {
    max-width: 384px;  /* 默认宽度 */
    /* 可以改为: 400px, 420px 等 */
}
```

#### 主图高度
```css
/* 找到 .hero-image-area 样式 */
.hero-image-area {
    height: 192px;  /* 默认高度 */
    /* 可以改为: 200px, 240px 等 */
}
```

#### 相册间距
```css
/* 找到 .gallery-grid 样式 */
.gallery-grid {
    gap: 16px;  /* 默认间距 */
    /* 可以改为: 12px, 20px 等 */
}
```

### 🔤 修改字体

#### 字体家族
```css
/* 在body样式中修改 */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', '您喜欢的字体', sans-serif;
```

#### 字体大小
```css
/* 主标题 */
.hero-title {
    font-size: 30px;  /* 可以调整 */
}

/* 副标题 */
.hero-subtitle {
    font-size: 14px;  /* 可以调整 */
}
```

## ⚙️ 管理面板使用

### 🔑 进入管理模式

1. **显示管理按钮**: 按键盘 `Ctrl+Shift+A`
2. **点击管理按钮**: 页面右下角出现的齿轮图标
3. **输入密码**: 默认 `qwe5566@`
4. **进入管理**: 弹出编辑窗口

### ✏️ 在线编辑

管理面板可以修改：
- 主标题
- 副标题（支持换行）
- 描述文字（支持换行）
- 三个文字介绍区域的标题和内容

**注意**: 管理面板只能修改文字内容，图片和链接需要在HTML中修改。

### 💾 保存机制

- **自动保存**: 点击"保存更改"后自动保存到浏览器本地存储
- **永久保存**: 只在当前浏览器生效，换浏览器需要重新设置
- **导出设置**: 可以在浏览器控制台运行以下代码导出设置：
  ```javascript
  console.log(JSON.stringify(localStorage.getItem('siteConfig')));
  ```

## 🔗 链接设置详解

### 📱 社交平台链接格式

#### Telegram
```javascript
// 普通链接
url: "https://t.me/您的用户名"

// 直接打开APP（手机端）
url: "tg://resolve?domain=您的用户名"
```

#### LINE
```javascript
// 添加好友链接
url: "https://line.me/ti/p/您的LINE-ID"

// 直接打开APP（手机端）
url: "line://ti/p/您的LINE-ID"
```

#### WhatsApp
```javascript
// 发送消息链接
url: "https://wa.me/您的电话号码"

// 预设消息
url: "https://wa.me/您的电话号码?text=Hello"
```

#### Instagram
```javascript
// 个人主页
url: "https://instagram.com/您的用户名"

// 直接打开APP（手机端）
url: "instagram://user?username=您的用户名"
```

### 📞 特殊链接类型

#### 电话链接
```javascript
url: "tel:+86138000000000"  // 点击直接拨打电话
```

#### 邮件链接
```javascript
url: "mailto:your@email.com"  // 点击打开邮件客户端
```

#### SMS短信
```javascript
url: "sms:+86138000000000"  // 点击发送短信
```

## 🚀 性能优化技巧

### 🖼️ 图片优化

1. **压缩图片**: 使用在线工具压缩图片大小
2. **选择合适格式**:
   - 照片用JPG
   - 图标用PNG
   - 简单图形用SVG
3. **控制尺寸**: 不要使用过大的图片

### ⚡ 加载优化

1. **图片懒加载**: 修改img标签添加 `loading="lazy"`
2. **压缩代码**: 移除不必要的空格和注释
3. **使用CDN**: 将图片放在CDN上加速访问

### 📱 移动端优化

1. **触摸友好**: 确保按钮足够大（最小44px）
2. **加载速度**: 控制页面总大小在1MB以内
3. **字体可读**: 确保最小字体不小于12px

## 🔍 SEO优化建议

### 📄 基础SEO

在HTML的 `<head>` 部分添加：

```html
<!-- 页面标题 -->
<title>您的网站标题 - 关键词</title>

<!-- 页面描述 -->
<meta name="description" content="不超过160字符的网站描述">

<!-- 关键词 -->
<meta name="keywords" content="关键词1,关键词2,关键词3">

<!-- 作者信息 -->
<meta name="author" content="您的名字">
```

### 🌐 社交分享优化

```html
<!-- Facebook/微信分享 -->
<meta property="og:title" content="您的网站标题">
<meta property="og:description" content="分享描述">
<meta property="og:image" content="https://您的域名.com/分享图片.jpg">
<meta property="og:url" content="https://您的域名.com">

<!-- Twitter分享 -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="您的网站标题">
<meta name="twitter:description" content="分享描述">
<meta name="twitter:image" content="https://您的域名.com/分享图片.jpg">
```

## 🛠️ 故障排除

### ❓ 常见问题

#### 图片不显示
**可能原因**:
- 图片链接失效
- 图片服务器限制外链
- 图片URL格式错误

**解决方法**:
1. 检查图片链接是否可以直接访问
2. 尝试换到其他图床服务
3. 确保URL是直链地址

#### 管理面板打不开
**可能原因**:
- 快捷键按错
- 浏览器阻止了JavaScript
- 密码输入错误

**解决方法**:
1. 确认按下 `Ctrl+Shift+A`
2. 检查浏览器是否允许JavaScript
3. 确认密码是否正确

#### 手机端显示异常
**可能原因**:
- 缺少viewport标签
- CSS媒体查询问题
- 图片尺寸过大

**解决方法**:
1. 确保包含viewport标签
2. 检查CSS响应式设置
3. 优化图片大小

#### 文字换行不正确
**可能原因**:
- 没有使用 `\n` 换行符
- CSS样式被覆盖

**解决方法**:
1. 在文字中使用 `\n` 进行换行
2. 确保CSS中有 `white-space: pre-line;`

### 🔧 调试技巧

#### 浏览器开发者工具
1. 按 `F12` 打开开发者工具
2. 查看Console面板的错误信息
3. 在Network面板检查资源加载情况

#### 测试方法
1. **不同设备**: 测试手机、平板、电脑
2. **不同浏览器**: 测试Chrome、Safari、Firefox
3. **不同网络**: 测试WiFi、4G网络环境

## 📞 获取帮助

### 🔗 有用资源
- **HTML教程**: https://www.w3school.com.cn/html/
- **CSS教程**: https://www.w3school.com.cn/css/
- **颜色选择器**: https://htmlcolorcodes.com/
- **图片压缩**: https://tinypng.com/

### 💬 技术支持
- **GitHub Issues**: 提交bug报告和功能建议
- **在线文档**: 查看最新使用说明
- **社区论坛**: 与其他用户交流经验

---

**希望这个指南能帮助您轻松定制出完美的韩式链接页面！** 🎉
