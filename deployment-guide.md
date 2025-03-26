# 梵慕学院网站部署指南

这份指南将帮助你将梵慕学院网站部署到GitHub并通过Vercel进行发布。即使你不懂编程，按照以下步骤操作也能轻松完成部署。

## 第一部分：准备网站文件

### 步骤1：创建网站文件结构

1. 在你的电脑上创建一个名为`vanmu-academy`的文件夹
2. 在这个文件夹内创建以下结构：
   ```
   vanmu-academy/
   ├── index.html
   ├── css/
   │   └── style.css
   ├── js/
   │   └── main.js
   └── images/
   ```

### 步骤2：复制文件内容

1. 将我提供的`index.html`内容复制到对应文件中
2. 将`style.css`内容复制到`css`文件夹下的对应文件中
3. 将`main.js`内容复制到`js`文件夹下的对应文件中

### 步骤3：准备网站图片

你需要准备以下图片，并放入`images`文件夹：

- `logo.svg` - 梵慕学院的logo
- `logo-white.svg` - 白色版本的logo（用于页脚）
- `hero-img.svg` - 首页主视觉图片
- `course-1.jpg` 到 `course-4.jpg` - 课程图片
- `philosophy.jpg` - 学院理念图片
- `master-1.jpg` 到 `master-3.jpg` - 名师照片
- `testimonial-1.jpg` 到 `testimonial-3.jpg` - 学员头像
- `qrcode.jpg` - 微信公众号二维码
- `favicon.png` - 网站图标

如果你没有这些图片，可以使用以下方法获取：

1. 使用免费图片网站如[Unsplash](https://unsplash.com/)或[Pexels](https://www.pexels.com/)下载适合的图片
2. 使用在线设计工具如[Canva](https://www.canva.com/)创建logo
3. 可以使用[svg波浪生成器](https://getwaves.io/)创建漂亮的SVG背景

## 第二部分：创建GitHub仓库

### 步骤1：注册GitHub账号

1. 访问[GitHub](https://github.com/)
2. 点击右上角的"Sign up"按钮注册账号
3. 按照指示填写信息并完成注册

### 步骤2：创建新仓库

1. 登录GitHub账号后，点击右上角的"+"图标，选择"New repository"
2. 仓库名称填写：`vanmu-academy`
3. 描述可以填写：`梵慕学院官方网站`
4. 选择"Public"（公开）
5. 勾选"Add a README file"（添加一个README文件）
6. 点击"Create repository"创建仓库

### 步骤3：上传文件到GitHub

有两种方法可以上传你的文件：

#### 方法1：通过GitHub网页上传（简单）

1. 在你的仓库页面，点击"Add file"按钮，选择"Upload files"
2. 拖拽你本地的`vanmu-academy`文件夹中的所有文件和文件夹到上传区域
3. 在"Commit changes"部分，添加描述："初始网站文件上传"
4. 点击"Commit changes"按钮完成上传

#### 方法2：使用GitHub Desktop（推荐）

1. 下载并安装[GitHub Desktop](https://desktop.github.com/)
2. 登录你的GitHub账号
3. 点击"File" > "Clone repository"，选择你刚创建的`vanmu-academy`仓库
4. 选择本地存储位置，点击"Clone"
5. 将你准备好的网站文件复制到克隆下来的文件夹中
6. 在GitHub Desktop中，你会看到变更列表
7. 在底部填写"Summary"（例如："初始网站文件上传"）
8. 点击"Commit to main"
9. 点击上方的"Push origin"将文件推送到GitHub

## 第三部分：使用Vercel部署网站

### 步骤1：注册Vercel账号

1. 访问[Vercel](https://vercel.com/)
2. 点击"Sign Up"注册账号
3. 建议使用GitHub账号登录，这样可以直接关联你的GitHub仓库

### 步骤2：导入GitHub项目

1. 登录Vercel后，点击"New Project"
2. 在"Import Git Repository"部分，找到并选择你的`vanmu-academy`仓库
3. 点击"Import"

### 步骤3：配置项目

1. 项目名称可以保持默认（`vanmu-academy`）或自定义
2. 默认配置通常即可，不需要更改任何设置
3. 点击"Deploy"开始部署

### 步骤4：查看部署结果

1. 等待几分钟，Vercel会自动部署你的网站
2. 部署成功后，你会看到一个预览链接，点击可