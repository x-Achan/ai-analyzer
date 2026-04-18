# 🚀 AI 赋能的智能简历分析系统 (AI Resume Analyzer)

本项目是一个基于大语言模型 (LLM) 和 Serverless 架构的全栈 HR 效率工具。通过 AI 技术实现简历的自动化结构化解析、深度信息提取以及岗位精准匹配评分。

## ✨ 核心亮点

- **📄 智能解析与清洗**：支持多页 PDF 简历上传，利用 `pdfplumber` 提取文本并进行自动化去噪与合理分段处理。
- **🧠 深度关键信息提取 (含加分项)**：超越基础字段，精准捕捉**求职意向、期望薪资、工作年限**及核心项目经历。
- **🎯 语义级精准匹配 (含加分项)**：基于智谱 GLM-4 模型，对简历与岗位需求 (JD) 进行双向语义对齐，输出 0-100 评分及详细的 AI 评估理由。
- **⚡ 多级缓存架构 (含加分项)**：
  - **后端缓存**：基于 MD5 哈希的内存级缓存，避免相同简历/岗位的重复 AI 计算，实现 0 延迟响应。
  - **前端持久化**：利用浏览器 `LocalStorage` 实现状态保持，用户刷新页面或重启浏览器后，无需重复上传即可查看上次结果。
- **🌐 云原生全栈部署**：
  - **前端**：采用 Vanilla JS + 响应式 CSS 架构，部署于 **GitHub Pages**。
  - **后端**：基于 Python FastAPI，通过函数计算 (FC) 部署于 **阿里云 Serverless** 平台。

## 🛠️ 技术栈
- **AI 模型**：智谱大模型 GLM-4-Flash
- **后端**：Python 3.9, FastAPI, Uvicorn, pdfplumber
- **前端**：HTML5, CSS3 (Flexbox/Grid), JavaScript (Fetch API)
- **部署**：阿里云函数计算 (FC), GitHub Pages

## 📖 使用方法

由于本项目后端部署在阿里云 Serverless 测试环境，出于安全协议（SSL/HTTPS）限制，请按照以下步骤进行首次访问激活：

### 1. 激活后端服务 (首次访问必做)
由于浏览器对自签名证书或临时域名的限制，请先点击下方的后端 API 激活链接：
👉 **[点击此处激活后端 API 引擎](https://fastapi-kja0.fcv3.1848055138812143.cn-beijing.fc.devsapp.net/docs)**

* **注意**：如果浏览器弹出“您的连接不是私密连接”，请点击页面上的 **“高级”** -> **“继续前往/访问”**。
* 看到绿色的 FastAPI 文档界面后，即可关闭该标签页。

### 2. 进入前端系统
点击进入部署在 GitHub Pages 的正式前端页面：
👉 **[进入 AI 简历分析系统](https://x-achan.github.io/ai-analyzer/)**

### 3. 操作流程
1.  **上传简历**：点击“选择文件”上传一份 PDF 格式的简历。
2.  **提取信息**：点击“上传并让 AI 提取信息”，系统将自动展示结构化后的“候选人画像”卡片。
3.  **输入需求**：在下方的文本框中输入你想要的岗位描述 (JD)。
4.  **开始评分**：点击“AI 简历匹配评分”，获取 0-100 的匹配分数、技能命中情况及 AI 详细评价。

---

## 📂 本地开发环境配置

如果你希望在本地运行本项目：

1.  **克隆仓库**：
    ```bash
    git clone https://github.com/x-achan/ai-analyzer.git
    cd ai-analyzer
    ```
2.  **安装依赖**：
    ```bash
    pip install fastapi uvicorn pdfplumber openai pydantic
    ```
3.  **配置 API Key**：
    打开 `index.py`，将 `API_KEY` 替换为你自己的智谱 AI Key。
4.  **启动后端**：
    ```bash
    python index.py
    ```
5.  **运行前端**：
    修改 `index.html` 中的 `API_BASE` 为 `http://127.0.0.1:9000`，直接双击打开 `index.html` 即可。