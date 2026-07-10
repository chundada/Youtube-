<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6&height=200&section=header&text=Video%20to%20Notes&fontSize=60&fontColor=fff&animation=fadeIn">
  <img alt="header" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6&height=200&section=header&text=Video%20to%20Notes&fontSize=60&fontColor=fff&animation=fadeIn">
</picture>

<div align="center">

# 🎬 Video to Notes

### 将 YouTube / Bilibili 视频转化为完整的学习文档

[![Python](https://img.shields.io/badge/Python-3.8+-blue?style=flat-square&logo=python&logoColor=white)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=flat-square)]()

</div>

---

## ✨ 功能亮点

| 功能 | 说明 |
|------|------|
| 🎯 **全自动字幕获取** | YouTube & Bilibili 自动识别，多级降级确保不空手而归 |
| 📝 **结构化学习笔记** | 不是摘要，是"过程还原式"学习文档——读一遍等于听了一遍课 |
| 📊 **可视化增强** | Mermaid 思维导图、对比表格、信息卡片，每个主题至少一张图 |
| 🎨 **精美 HTML** | 深色主题、响应式设计、零外部依赖，可离线打开 |
| 📂 **文件夹交付** | 自动输出到桌面 `学习笔记产出/` 文件夹，即开即读 |
| 🌐 **跨平台** | Windows / macOS / Linux 全支持 |

---

## 🚀 快速开始

### 安装

```bash
# 克隆仓库
git clone https://github.com/chundada/video-to-notes.git
cd video-to-notes

# 安装依赖
pip install -r requirements.txt
```

### 下载字幕

```bash
# YouTube 视频
python scripts/fetch_transcript.py https://www.youtube.com/watch?v=xxxxx

# Bilibili 视频
python scripts/fetch_transcript.py https://www.bilibili.com/video/BVxxxxxxxxxx

# 直接输出到桌面
python scripts/fetch_transcript.py https://youtu.be/xxxxx --to-desktop

# 指定语言
python scripts/fetch_transcript.py <URL> --lang zh-Hans
```

### 生成学习文档

把视频链接交给 AI（配合本仓库的 Skill 指令），AI 会自动：

1. 📥 运行脚本获取完整字幕
2. 🔍 分析内容结构，识别主题和关键论点
3. 📝 撰写"过程还原式"学习文档（先过程，后结论）
4. 🎨 生成带 Mermaid 导图和可视化的 HTML
5. 📂 交付到 `桌面/学习笔记产出/{视频标题}_学习笔记/`

---

## 📂 项目结构

```
video-to-notes/
├── 📁 scripts/                        # 工具脚本
│   └── fetch_transcript.py            # 字幕下载（YouTube / Bilibili）
├── 📁 skill/                          # AI 工作流指令
│   └── YouTube学习笔记生成器_Skill_v3.md  # 完整的 AI 操作手册
├── 📄 README.md                       # 本文件
├── 📄 requirements.txt                # Python 依赖
└── 📄 .gitignore                      # Git 忽略规则
```

---

## 📖 Skill 说明

[skill/YouTube学习笔记生成器_Skill_v3.md](skill/YouTube学习笔记生成器_Skill_v3.md) 是这份工作流的核心——一份给 AI 阅读的完整操作手册，包含：

- ✅ **视频类型判断** — 授课/访谈/教程/故事，四种类型四种写法
- ✅ **多级降级策略** — 字幕获取失败后的三级备用方案，永不空手
- ✅ **预扫描清单** — 人名、书名、案例、数据、引语——一项都不能漏
- ✅ **主题切分规则** — 每个主题 4-6 个子论点，按逻辑切分不按时均分
- ✅ **过程还原式写作** — 先走完推导过程，结论在末尾自然浮现
- ✅ **可视化规范** — 每个主题至少 1 个图表，全文至少 1 个全局导图
- ✅ **学习增强模块** — 概念速查表、行动指南、延伸阅读、金句卡片
- ✅ **自审清单** — 写完逐条核对的 30+ 项检查，通不过就返工
- ✅ **引语翻译规则** — 所有英文引语下方附中文翻译

---

## 🛠️ 脚本功能

`scripts/fetch_transcript.py` 支持：

| 功能 | 状态 |
|------|------|
| YouTube 字幕（youtube-transcript-api） | ✅ 首选 |
| YouTube 字幕（yt-dlp 降级） | ✅ 自动降级 |
| Bilibili 字幕 | ✅ 自动识别 |
| 自动平台识别 | ✅ |
| 跨平台桌面交付 | ✅ `--to-desktop` |
| 网络重试机制 | ✅ `--retry N` |
| 多格式输出（JSON / TXT / 时间戳 / 元数据） | ✅ |
| 指定字幕语言 | ✅ `--lang` |

---

## 📦 依赖

| 包名 | 用途 | 必需 |
|------|------|:----:|
| `youtube-transcript-api` | YouTube 字幕获取（首选） | ✅ |
| `requests` | 视频元数据获取 | ✅ |
| `yt-dlp` | YouTube 降级 + Bilibili 字幕 | ✅ |
| `markdown` | Markdown → HTML 降级输出 | ❌ 可选 |

---

## 🌐 跨平台

| 项目 | Windows | macOS / Linux |
|------|---------|---------------|
| Python | `python` | `python3` |
| 路径分隔符 | `\` | `/` |
| 桌面路径 | `C:\Users\{用户名}\Desktop\学习笔记产出\` | `~/Desktop/学习笔记产出/` |

> 脚本已内置跨平台适配，`--to-desktop` 参数自动检测桌面路径。

---

## 📝 输出示例

学习文档交付到 `桌面/学习笔记产出/` 后，目录结构如下：

```
桌面/学习笔记产出/
└── 姜教授第三次世界大战_学习笔记/
    ├── 姜教授第三次世界大战_学习笔记.html   ← 主文档（直接浏览器打开）
    ├── BTJGr78-zyw_transcript.json            ← 字幕（带时间戳结构）
    ├── BTJGr78-zyw_transcript.txt             ← 字幕（纯文本）
    ├── BTJGr78-zyw_timestamped.txt            ← 字幕（带时间戳文本）
    └── BTJGr78-zyw_info.json                  ← 视频元数据
```

HTML 文档特性：
- 🌙 深色主题，护眼排版
- 📱 响应式设计，手机/平板/桌面都可读
- 🖨️ 支持打印样式
- 🔗 零外部依赖，可离线打开
- 🗺️ 内置 Mermaid 思维导图
- 📊 对比表格、信息卡片、引用区块

---

## 🤝 贡献

欢迎提 Issue 或 PR！如果你有好的改进建议，请随时联系。

---

<div align="center">
  <sub>Made with ❤️ for learners worldwide</sub>
</div>
