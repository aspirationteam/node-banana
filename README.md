# Node Banana

> **Important note:** This is in early development and hasn't been tested off my machines,it probably has some issues. Use Chrome. 

Node Banana is node-based workflow application for generating images with NBP. Build image generation pipelines by connecting nodes on a visual canvas. Built mainly with Opus 4.5.

## 项目说明（中文）

Node Banana 是一款节点式工作流工具，通过在画布上拖拽并连接节点，就能快速搭建图像/文本生成流程，适合需要复用、组合 AI 能力的创作者。

### 主要功能

- **可视化流程编辑**：无限画布、拖拽节点、平移缩放皆可。
- **图像标注&拆分**：内置矩形、箭头、手绘等标注工具，可用于描述或拆分素材。
- **AI 生成能力**：调用 Google Gemini 生成图像，也能用 Gemini 或 OpenAI 生成文本。
- **工作流串联**：同类输入输出自动匹配，可自由搭建复杂链路。
- **保存/恢复**：工作流支持导出 JSON，亦可再次导入继续编辑。

### 技术栈

- Next.js 16（App Router） + TypeScript
- React Flow（@xyflow/react）负责节点画布
- Konva.js / react-konva 实现标注
- Zustand 状态管理，Tailwind CSS 负责样式
- Google Gemini / OpenAI API 提供 AI 推理

### 快速上手

1. 安装依赖：`npm install`
2. 配置 `.env.local`，至少填入 `GEMINI_API_KEY`，如需 OpenAI 再补 `OPENAI_API_KEY`
3. 启动开发环境：`npm run dev`，浏览器访问 `http://localhost:3000`
4. 在浮动面板添加节点、拖线连接、配置参数，完成后点击 Run 即可运行
5. 想要复用工作流，可在页面右上角导出并保存 JSON

## Features

- **Visual Node Editor** - Drag-and-drop nodes onto an infinite canvas with pan and zoom
- **Image Annotation** - Full-screen editor with drawing tools (rectangles, circles, arrows, freehand, text)
- **AI Image Generation** - Generate images using Google Gemini models
- **Text Generation** - Generate text using Google Gemini or OpenAI models
- **Workflow Chaining** - Connect multiple nodes to create complex pipelines
- **Save/Load Workflows** - Export and import workflows as JSON files

## Tech Stack

- **Framework**: Next.js 16 (App Router)
- **Language**: TypeScript
- **Node Editor**: @xyflow/react (React Flow)
- **Canvas**: Konva.js / react-konva
- **State Management**: Zustand
- **Styling**: Tailwind CSS
- **AI**: Google Gemini API, OpenAI API

## Getting Started

### Prerequisites

- Node.js 18+
- npm

### Environment Variables

Create a `.env.local` file in the root directory:

```env
GEMINI_API_KEY=your_gemini_api_key
OPENAI_API_KEY=your_openai_api_key  # Optional, for OpenAI LLM provider
```

### Installation

```bash
npm install
```

### Development

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

### Build

```bash
npm run build
npm run start
```

## Example Workflows

The `/examples` directory contains some example workflow files from my personal projects. To try them:

1. Start the dev server with `npm run dev`
2. Drag any `.json` file from the `/examples` folder into the browser window
3. Make sure you review each of the prompts before starting, these are fairly targetted to the examples. 

## Usage

1. **Add nodes** - Click the floating action bar to add nodes to the canvas
2. **Connect nodes** - Drag from output handles to input handles (matching types only)
3. **Configure nodes** - Adjust settings like model, aspect ratio, or drawing tools
4. **Run workflow** - Click the Run button to execute the pipeline
5. **Save/Load** - Use the header menu to save or load workflows

## Connection Rules

- **Image** handles connect to **Image** handles only
- **Text** handles connect to **Text** handles only
- Image inputs on generation nodes accept multiple connections
- Text inputs accept single connections

## License

MIT
