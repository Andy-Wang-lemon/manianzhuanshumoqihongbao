# 马年专属默契红包

一个充满创意的新年红包 Web 应用，让你通过默契度测试来发送特别的新年祝福！

## 项目简介

这是一个纯前端的单页面应用，可以让你制作专属的新年默契红包。通过设计6道默契测试题，考验对方对你的了解程度，答对题目越多，能拆的红包就越多！完美适合春节期间与家人、朋友互动。

### 核心功能

-  **自定义题目**: 设计6道专属的默契测试题
-  **礼物设置**: 最多设置3个红包奖励
-  **一键分享**: 生成压缩链接，方便分享给好友
-  **默契评分**: 根据答题正确率计算默契度
-  **精美动效**: 烟花、呼吸动画、红包拆开效果等
-  **移动优先**: 完美适配手机屏幕

##  使用流程

### 发起人（制作红包）

1. 填写基本信息：你的名字和收件人名字
2. 设计6道默契测试题，每题3个选项
3. 设置1-3个礼物奖励
4. 点击"生成专属红包"，复制链接分享给好友

### 接收人（拆红包）

1. 打开链接，查看专属红包封面
2. 点击"拆"按钮开始答题
3. 完成6道题目，查看默契度评分
4. 根据表现获得拆红包机会（1-5个）
5. 点击红包逐个拆开，获取礼物

##  快速开始

### 方式一：直接双击运行

#### macOS 用户
```bash
# 双击运行
./run-mac.sh

# 或在终端执行
bash run-mac.sh
```

#### Windows 用户
```batch
# 双击运行
run-win.bat

# 或在命令提示符中执行
run-win.bat
```

脚本会自动：
- 检测系统中可用的服务器（PHP/Ruby/Python）
- 启动本地服务器（默认端口 8080）
- 自动打开浏览器访问应用

### 方式二：手动启动

使用任意 HTTP 服务器运行 `frontend/public/index.html`

#### 使用 Python
```bash
cd frontend/public
python3 -m http.server 8080
```

#### 使用 PHP
```bash
cd frontend/public
php -S localhost:8080
```

#### 使用 Node.js
```bash
cd frontend/public
npx serve -p 8080
```

然后在浏览器访问: `http://localhost:8080`

##  项目结构

```
web马年专属默契红包/
├── frontend/
│   └── public/
│       └── index.html          # 主应用文件（单页面应用）
├── run-mac.sh                  # macOS 启动脚本
├── run-win.bat                 # Windows 启动脚本
├── local-server.ps1            # PowerShell 本地服务器
├── install.sh                  # 依赖安装脚本
└── README.md                   # 项目说明文档
```

##  技术栈

- **纯前端实现**: 无需后端服务器
- **Tailwind CSS**: 现代化的样式框架
- **Canvas API**: 烟花动画效果
- **LZ-String**: 数据压缩算法，缩短分享链接
- **LocalStorage**: 草稿自动保存
- **URL Hash**: 数据通过 URL 传递，无需数据库

##  技术亮点

### 1. 智能数据压缩
使用 LZ-String 算法对数据进行压缩，配合 Base64 编码，使分享链接更短：
```javascript
// 数据结构简化（使用单字符key）
const compactData = {
    s: sender,      // 发送人
    r: receiver,    // 接收人
    g: gifts,       // 礼物列表
    q: questions    // 题目列表
};
// LZ压缩 + Base64编码
const compressed = LZString.compressToBase64(JSON.stringify(compactData));
```

### 2. 草稿自动保存
制作红包过程中，数据自动保存到 LocalStorage，防止意外丢失：
```javascript
localStorage.setItem('redpacket_draft', JSON.stringify(data));
```

### 3. 响应式设计
使用媒体查询和 viewport-fit，完美适配各种手机屏幕，包括刘海屏：
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no, viewport-fit=cover">
```

### 4. 精美动画效果
- 烟花粒子系统（Canvas）
- CSS3 呼吸动画
- 红包抖动效果
- 页面切换过渡

##  界面预览

应用包含以下页面：

1. **制作页面** - 填写信息、设计题目、设置礼物
2. **封面页面** - 展示专属红包，吸引接收人打开
3. **答题页面** - 6道默契测试题，带进度条
4. **结果页面** - 显示默契度评分和可拆红包数量
5. **拆红包页面** - 互动式拆红包体验
6. **总结页面** - 展示所有获得的礼物

##  默契度计算规则

```
答对题目数 → 可拆红包数量
0-1 题    → 1 个红包
2-3 题    → 2 个红包
4 题      → 3 个红包
5 题      → 4 个红包
6 题      → 5 个红包（全对奖励）
```

```
默契度百分比 = (答对题目数 / 6) × 100%

< 60%     → "即使默契还在培养,心意永远满分！"
60%-89%   → "这默契度,不愧是这种关系！"
≥ 90%     → "天哪！你简直是肚子里的蛔虫！"
```

##  浏览器兼容性

- ✅ Chrome/Edge (推荐)
- ✅ Safari (iOS/macOS)
- ✅ Firefox
- ✅ 微信内置浏览器
- ✅ 其他现代浏览器

##  最佳使用体验

- 推荐在**手机**上使用（已针对移动端优化）
- 支持添加到主屏幕，像 App 一样使用
- 建议使用**竖屏**浏览
- 在微信中分享链接给好友体验最佳

##  使用场景

-  **春节红包**: 给家人朋友发新年祝福
-  **生日惊喜**: 测试对寿星的了解程度
-  **情侣互动**: 考验彼此的默契度
-  **家庭聚会**: 增进家人之间的了解
-  **节日庆祝**: 任何需要红包互动的场合

##  隐私说明

- ✅ **纯前端应用**: 所有数据在浏览器本地处理
- ✅ **无服务器存储**: 不上传任何数据到服务器
- ✅ **URL传递**: 数据通过加密压缩后的URL分享
- ✅ **本地草稿**: 制作过程中的草稿仅保存在本地浏览器

##  开源协议

本项目仅供学习交流使用。

##  致谢

- 设计灵感来自传统红包文化
- 使用了 [Tailwind CSS](https://tailwindcss.com/) 样式框架
- 使用了 [LZ-String](https://github.com/pieroxy/lz-string) 压缩库

##  问题反馈

如果您在使用过程中遇到任何问题，欢迎提出反馈！

---

<div align="center">

 **祝您新年快乐，马年大吉！** 

Made with ❤️ by HAISNAP

</div>
