# SBT Token Landing Page

Soul Bound Tokens - 基于 CZ's Giggle 白皮书的下一代 Meme Token

## 🚀 部署到 Vercel（实现 junction.link/mh 访问）

### 方案一：独立项目部署 + 自定义域名
如果你拥有 `junction.link` 域名，这是推荐的方式：

1. **推送到 GitHub**
   ```bash
   # 如果还没有提交，先提交
   git add .
   git commit -m "Initial commit: SBT Token landing page"
   
   # 在 GitHub 上创建仓库后，关联并推送
   git remote add origin https://github.com/你的用户名/仓库名.git
   git branch -M main
   git push -u origin main
   ```

2. **在 Vercel 上部署**
   - 访问 [vercel.com](https://vercel.com) 并登录
   - 点击 "Add New Project"
   - 导入你的 GitHub 仓库
   - 点击 "Deploy"

3. **配置自定义域名为 junction.link**
   - 在 Vercel 项目设置中，进入 "Domains"
   - 添加域名：`junction.link`
   - 按照提示配置 DNS 记录（添加 A 记录或 CNAME 记录）
   - 等待 DNS 生效后，访问 `https://junction.link/mh` 即可

### 方案二：如果 junction.link 已经有主站
如果 `junction.link` 已经部署了其他网站：

#### 选项 A：主站也在 Vercel 上
1. 将此 SBT 项目部署到 Vercel（会获得一个临时域名如 `sbt-token.vercel.app`）
2. 在主站项目的 `vercel.json` 中添加重写规则：
   ```json
   {
     "rewrites": [
       {
         "source": "/mh/:path*",
         "destination": "https://sbt-token.vercel.app/:path*"
       }
     ]
   }
   ```

#### 选项 B：主站在其他平台
1. 部署此项目到 Vercel，获得临时域名
2. 在主站的服务器/平台配置中，添加反向代理或重写规则，将 `/mh` 路径代理到 Vercel 临时域名

### 方案三：使用子域名
如果路径方式太复杂，也可以使用子域名：
- 部署后配置域名为 `mh.junction.link`
- 修改 `index.html` 第6行的 `<base href="/mh/">` 改为 `<base href="/">`

## 📝 文件说明

- `index.html` - 主页面（已配置 `/mh` 子路径）
- `111.png` - SBT Token Logo
- `1.jpg` - Featured Meme 图片
- `vercel.json` - Vercel 部署配置（支持 `/mh` 路径访问）

## 🔧 本地测试

要在本地测试子路径效果，可以使用：

```bash
# 使用 Python 启动本地服务器
python -m http.server 8000

# 然后访问 http://localhost:8000/mh
```

**注意**：由于配置了 `<base href="/mh/">`，直接访问 `http://localhost:8000/index.html` 可能会导致资源加载问题。

## 🌐 当前配置

- 域名路径：`https://junction.link/mh`
- Base URL：`/mh/`
- 资源路径会自动加上 `/mh/` 前缀

## 💡 重要提示

如果 Vercel 部署后访问 `域名/mh` 出现 404：

1. 检查 `vercel.json` 是否正确上传
2. 在 Vercel 项目设置中，检查 "Output Directory" 是否为空（应该是根目录）
3. 确认访问的是 `https://你的域名/mh` 而不是 `https://你的域名/mh/index.html`

## 📞 Contract Address

```
0x0afe2bd3f79dedc3ee913be524ecafd9470b4444
```

---

Made with 🚀 for the SBT Community

