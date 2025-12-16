# Node Banana

[English](README.md) | [中文](README.zh-CN.md)

> **重要提示：** 项目仍处于早期阶段，只在作者的设备上做过有限测试，可能存在各种问题。推荐使用 Chrome。

Node Banana 是一款基于节点的工作流应用，可以在可视化画布上拖拽、连接节点来构建图像或文本的生成流程，尤其适合想要复用、组合 AI 能力的创作者。

## 主要特性

- **可视化节点编辑器**：无限画布支持拖拽、缩放和平移，工作流结构一目了然。
- **图像标注工具**：提供矩形、圆形、箭头、自由绘制和文字等多种标注方式。
- **AI 图像生成**：集成 Google Gemini 模型，可根据提示词生成图片。
- **AI 文本生成**：支持 Google Gemini 或 OpenAI 进行文本生成。
- **工作流串联**：连接节点的输入输出即可搭建复杂管线，适合多步骤推理。
- **保存/加载**：可将工作流导出为 JSON，也能在后续导入继续修改。

## 技术栈

- **框架**：Next.js 16（App Router）
- **语言**：TypeScript
- **节点画布**：@xyflow/react（React Flow）
- **标注画布**：Konva.js / react-konva
- **状态管理**：Zustand
- **样式**：Tailwind CSS
- **AI 接口**：Google Gemini API、OpenAI API

## 快速开始

### 环境要求

- Node.js 18 或更高版本
- npm

### 环境变量

在项目根目录创建 `.env.local`：

```env
GEMINI_API_KEY=你的_gemini_api_key
OPENAI_API_KEY=你的_openai_api_key # 可选，用于 OpenAI 供应商
```

### 安装依赖

```bash
npm install
```

### 启动开发环境

```bash
npm run dev
```

在浏览器中打开 [http://localhost:3000](http://localhost:3000)。

### 构建产物

```bash
npm run build
npm run start
```

## 示例工作流

`/examples` 目录包含若干示例 JSON：

1. 运行 `npm run dev`
2. 将任意 `.json` 文件拖进浏览器窗口
3. 查看并按需修改提示词后再运行

## 使用指南

1. **添加节点**：通过浮动操作栏添加需要的节点。
2. **连接节点**：从输出端拖动到目标输入端（类型需匹配）。
3. **配置节点**：根据需求调整模型、比例、分辨率或标注内容。
4. **执行流程**：点击 Run 按钮运行整个工作流。
5. **保存/导入**：使用右上角菜单保存或加载 JSON 工作流。

## 连接规则

- **Image** 句柄只能连接到 **Image** 句柄
- **Text** 句柄只能连接到 **Text** 句柄
- 生成类节点的图像输入支持多条连接
- 文本输入默认只允许单条连接

## 许可

MIT
