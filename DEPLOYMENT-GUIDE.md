# 🚀 部署指南 - 韩式链接页面

本文档详细介绍如何将您的韩式链接页面部署到各种平台。

## 🌐 免费部署平台

### 1. GitHub Pages (推荐)

**优势**: 免费、稳定、支持自定义域名

```bash
# 步骤：
1. Fork本仓库到您的GitHub账号
2. 进入仓库设置 Settings → Pages
3. Source选择 "Deploy from a branch"
4. Branch选择 "main"
5. 文件夹选择 "/ (root)"
6. 点击Save

# 访问地址：
https://您的用户名.github.io/korean-html-complete/
```

**自定义域名**:
1. 在仓库根目录创建 `CNAME` 文件
2. 文件内容写入您的域名: `yourdomain.com`
3. 在域名DNS设置中添加CNAME记录指向 `您的用户名.github.io`

### 2. Netlify

**优势**: 拖拽部署、自动构建、表单处理

```bash
# 方法一：拖拽部署
1. 访问 netlify.com
2. 将 korean-html-complete 文件夹拖拽到部署区域
3. 等待部署完成，获得随机域名

# 方法二：Git集成
1. 连接GitHub仓库
2. 选择分支: main
3. 构建设置留空（静态文件无需构建）
4. 点击Deploy
```

**自定义域名**:
1. 在Netlify控制台选择 Domain settings
2. 添加自定义域名
3. 按照提示设置DNS记录

### 3. Vercel

**优势**: 全球CDN、自动HTTPS、性能优化

```bash
# 部署步骤：
1. 访问 vercel.com
2. 导入GitHub仓库
3. 项目设置保持默认
4. 点击Deploy
5. 等待部署完成
```

### 4. Surge.sh

**优势**: 命令行部署、简单快速

```bash
# 安装Surge
npm install -g surge

# 部署
cd korean-html-complete
surge

# 按提示设置域名和邮箱
```

## 🏢 私有服务器部署

### 1. IIS (Windows服务器)

**适用**: Windows Server环境

#### 准备工作
```bash
# 1. 启用IIS功能
# 控制面板 → 程序 → 启用或关闭Windows功能 → IIS

# 2. 创建网站目录
C:\inetpub\wwwroot\yoursite\
```

#### 部署步骤
1. **复制文件**到 `C:\inetpub\wwwroot\yoursite\`
2. **创建web.config**:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <defaultDocument>
            <files>
                <clear />
                <add value="index.html" />
            </files>
        </defaultDocument>

        <staticContent>
            <remove fileExtension=".css" />
            <remove fileExtension=".js" />
            <remove fileExtension=".png" />
            <remove fileExtension=".jpg" />
            <remove fileExtension=".svg" />

            <mimeMap fileExtension=".css" mimeType="text/css" />
            <mimeMap fileExtension=".js" mimeType="application/javascript" />
            <mimeMap fileExtension=".png" mimeType="image/png" />
            <mimeMap fileExtension=".jpg" mimeType="image/jpeg" />
            <mimeMap fileExtension=".svg" mimeType="image/svg+xml" />
        </staticContent>

        <httpErrors errorMode="Custom">
            <remove statusCode="404" />
            <error statusCode="404" path="index.html" responseMode="File" />
        </httpErrors>
    </system.webServer>
</configuration>
```

3. **设置权限**:
   - 右键网站文件夹 → 属性 → 安全
   - 添加 `IIS_IUSRS` 和 `IUSR` 用户
   - 给予读取权限

4. **创建网站**:
   - 打开IIS管理器
   - 右键"网站" → 添加网站
   - 网站名称: yoursite
   - 物理路径: `C:\inetpub\wwwroot\yoursite\`
   - 端口: 80

### 2. Apache (Linux服务器)

**适用**: Ubuntu/CentOS等Linux环境

#### 安装Apache
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install apache2

# CentOS/RHEL
sudo yum install httpd
sudo systemctl start httpd
sudo systemctl enable httpd
```

#### 部署步骤
```bash
# 1. 复制文件
sudo cp -r korean-html-complete/* /var/www/html/

# 2. 设置权限
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/

# 3. 创建.htaccess (可选)
sudo nano /var/www/html/.htaccess
```

**.htaccess 内容**:
```apache
DirectoryIndex index.html

# 启用压缩
<IfModule mod_deflate.c>
    AddOutputFilterByType DEFLATE text/html text/css application/javascript
</IfModule>

# 设置缓存
<IfModule mod_expires.c>
    ExpiresActive on
    ExpiresByType image/png "access plus 1 month"
    ExpiresByType image/jpg "access plus 1 month"
    ExpiresByType text/css "access plus 1 month"
    ExpiresByType application/javascript "access plus 1 month"
</IfModule>

# 错误页面
ErrorDocument 404 /index.html
```

#### 虚拟主机配置
```bash
# 创建虚拟主机配置
sudo nano /etc/apache2/sites-available/yoursite.conf
```

**虚拟主机配置内容**:
```apache
<VirtualHost *:80>
    ServerName yourdomain.com
    ServerAlias www.yourdomain.com
    DocumentRoot /var/www/html

    <Directory /var/www/html>
        AllowOverride All
        Require all granted
    </Directory>

    ErrorLog ${APACHE_LOG_DIR}/yoursite_error.log
    CustomLog ${APACHE_LOG_DIR}/yoursite_access.log combined
</VirtualHost>
```

```bash
# 启用网站
sudo a2ensite yoursite.conf
sudo systemctl reload apache2
```

### 3. Nginx (高性能服务器)

**适用**: 高并发、高性能需求

#### 安装Nginx
```bash
# Ubuntu/Debian
sudo apt update
sudo apt install nginx

# CentOS/RHEL
sudo yum install nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```

#### 配置文件
```bash
# 编辑Nginx配置
sudo nano /etc/nginx/sites-available/yoursite
```

**Nginx配置内容**:
```nginx
server {
    listen 80;
    server_name yourdomain.com www.yourdomain.com;
    root /var/www/yoursite;
    index index.html;

    # 启用Gzip压缩
    gzip on;
    gzip_types text/css application/javascript image/png image/jpg;

    # 设置缓存
    location ~* \.(css|js|png|jpg|jpeg|gif|svg)$ {
        expires 30d;
        add_header Cache-Control "public, immutable";
    }

    # HTML文件不缓存
    location ~* \.html$ {
        expires -1;
        add_header Cache-Control "no-cache, no-store, must-revalidate";
    }

    # 404错误处理
    error_page 404 /index.html;

    # 安全头部
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-XSS-Protection "1; mode=block" always;
}
```

```bash
# 启用网站
sudo ln -s /etc/nginx/sites-available/yoursite /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx

# 复制文件
sudo mkdir -p /var/www/yoursite
sudo cp -r korean-html-complete/* /var/www/yoursite/
sudo chown -R www-data:www-data /var/www/yoursite
```

## 🔒 HTTPS配置

### 使用Let's Encrypt (免费SSL)

#### Apache + Certbot
```bash
# 安装Certbot
sudo apt install certbot python3-certbot-apache

# 获取SSL证书
sudo certbot --apache -d yourdomain.com -d www.yourdomain.com

# 自动续期
sudo crontab -e
# 添加: 0 12 * * * /usr/bin/certbot renew --quiet
```

#### Nginx + Certbot
```bash
# 安装Certbot
sudo apt install certbot python3-certbot-nginx

# 获取SSL证书
sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
```

## 🌍 CDN加速

### 1. Cloudflare (推荐)

**免费方案包含**:
- 全球CDN加速
- DDoS防护
- SSL证书
- 缓存优化

**设置步骤**:
1. 注册Cloudflare账号
2. 添加您的域名
3. 更改域名DNS服务器到Cloudflare
4. 开启"代理状态"(橙色云朵)

### 2. 其他CDN服务
- **AWS CloudFront**: 适合AWS生态
- **阿里云CDN**: 适合中国用户
- **腾讯云CDN**: 性价比较高
- **七牛云**: 免费额度较多

## 📊 性能优化

### 1. 图片优化

```bash
# 压缩图片
npm install -g imagemin-cli

# 批量压缩PNG
imagemin images/*.png --out-dir=images-optimized --plugin=pngquant

# 批量压缩JPG
imagemin images/*.jpg --out-dir=images-optimized --plugin=mozjpeg
```

### 2. 代码压缩

**HTML压缩**:
```javascript
// 移除注释和多余空格
// 在部署前手动处理或使用在线工具
```

**图片懒加载**:
```html
<!-- 修改HTML中的img标签 -->
<img src="placeholder.jpg" data-src="real-image.jpg" loading="lazy">
```

### 3. 缓存策略

**浏览器缓存**:
```apache
# Apache .htaccess
<IfModule mod_expires.c>
    ExpiresActive on
    ExpiresByType text/html "access plus 0 seconds"
    ExpiresByType text/css "access plus 1 year"
    ExpiresByType application/javascript "access plus 1 year"
    ExpiresByType image/png "access plus 1 year"
</IfModule>
```

## 🔍 SEO优化

### 1. Meta标签优化

在HTML `<head>` 中添加:
```html
<!-- 基础SEO -->
<meta name="description" content="您的网站描述，不超过160字符">
<meta name="keywords" content="关键词1,关键词2,关键词3">
<meta name="author" content="您的名字">

<!-- Open Graph (社交分享) -->
<meta property="og:title" content="您的网站标题">
<meta property="og:description" content="您的网站描述">
<meta property="og:image" content="https://yourdomain.com/share-image.jpg">
<meta property="og:url" content="https://yourdomain.com">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="您的网站标题">
<meta name="twitter:description" content="您的网站描述">
<meta name="twitter:image" content="https://yourdomain.com/share-image.jpg">
```

### 2. 结构化数据

```html
<!-- JSON-LD结构化数据 -->
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "您的名字",
  "url": "https://yourdomain.com",
  "sameAs": [
    "https://t.me/yourusername",
    "https://line.me/ti/p/yourlineid"
  ]
}
</script>
```

## 📈 监控和分析

### 1. Google Analytics

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

### 2. 百度统计

```html
<!-- 百度统计代码 -->
<script>
var _hmt = _hmt || [];
(function() {
  var hm = document.createElement("script");
  hm.src = "https://hm.baidu.com/hm.js?您的统计ID";
  var s = document.getElementsByTagName("script")[0];
  s.parentNode.insertBefore(hm, s);
})();
</script>
```

## 🚨 常见问题

### 1. 文件权限问题
```bash
# Linux服务器权限设置
sudo chown -R www-data:www-data /var/www/yoursite
sudo chmod -R 755 /var/www/yoursite
```

### 2. 端口被占用
```bash
# 检查端口占用
sudo netstat -tulpn | grep :80

# 停止占用进程
sudo systemctl stop apache2
# 或
sudo systemctl stop nginx
```

### 3. 域名解析问题
```bash
# 检查DNS解析
nslookup yourdomain.com
dig yourdomain.com

# 检查网站可访问性
curl -I https://yourdomain.com
```

### 4. SSL证书问题
```bash
# 检查证书状态
sudo certbot certificates

# 手动续期
sudo certbot renew

# 强制续期
sudo certbot renew --force-renewal
```

## 📞 技术支持

如果您在部署过程中遇到问题：

1. **检查错误日志**:
   - Apache: `/var/log/apache2/error.log`
   - Nginx: `/var/log/nginx/error.log`
   - IIS: `C:\inetpub\logs\LogFiles\`

2. **在线工具**:
   - SSL检查: https://www.ssllabs.com/ssltest/
   - 网站速度: https://pagespeed.web.dev/
   - DNS检查: https://dnschecker.org/

3. **获取帮助**:
   - GitHub Issues: 提交问题和bug报告
   - 社区论坛: 寻求技术支持

---

**祝您部署顺利！** 🎉
