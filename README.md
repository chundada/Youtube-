# YouTube / Bilibili 学习笔记工具

将 YouTube 或 Bilibili 授课/访谈视频转化为完整的学习文档（HTML）。

## 项目结构

```
YouTube学习笔记工具/
├── 技能说明/
│   └── YouTube学习笔记生成器_Skill_v3.md   ← 技能说明（给 AI 用的完整指令）
├── scripts/
│   └── fetch_transcript.py                 ← 字幕下载脚本（跨平台）
├── requirements.txt                        ← 依赖清单（统一管理）
└── README.md                               ← 本文件
```

## 快速开始

### 1. 安装依赖

```bash
# 一次性安装所有必需依赖（推荐）
pip install -r requirements.txt

# 或手动安装
pip install youtube-transcript-api yt-dlp requests
```

### 2. 下载字幕

```bash
# YouTube
python scripts/fetch_transcript.py https://www.youtube.com/watch?v=xxxxx

# Bilibili
python scripts/fetch_transcript.py https://www.bilibili.com/video/BVxxxxxxxxxx

# 直接输出到桌面
python scripts/fetch_transcript.py https://youtu.be/xxxxx --to-desktop

# 指定语言 + 输出目录
python scripts/fetch_transcript.py <URL> --lang zh-Hans --output ./videos
```

### 3. 交付给 AI

把视频链接 + "做学习笔记" 丢给 AI，它会：
1. 运行脚本获取字幕
2. 分析内容
3. 生成 HTML 学习文档
4. 打包 ZIP 到桌面

## 跨平台说明

| 项目 | Windows | macOS |
|------|---------|-------|
| Python 命令 | `python` 或 `py` | `python3` |
| 路径分隔符 | `\` | `/` |
| 脚本运行 | `python scripts\fetch_transcript.py` | `python3 scripts/fetch_transcript.py` |
| 桌面路径 | `C:\Users\{用户名}\Desktop\` | `~/Desktop/` |

> `fetch_transcript.py` 已内置跨平台适配，使用 `--to-desktop` 参数会自动检测操作系统桌面路径。

## 脚本功能一览

`scripts/fetch_transcript.py` 支持：
- ✅ YouTube 字幕获取（首选 `youtube-transcript-api`，失败自动降级 `yt-dlp`）
- ✅ Bilibili 字幕获取（自动用 `yt-dlp`）
- ✅ 自动识别视频平台（YouTube / Bilibili）
- ✅ 跨平台桌面交付（`--to-desktop`）
- ✅ 网络重试机制（`--retry N`）
- ✅ 多种输出格式（JSON / TXT / 时间戳文本 / 元数据）

## 依赖说明

| 包名 | 用途 | 必需 |
|------|------|------|
| `youtube-transcript-api` | YouTube 字幕获取（首选） | 是 |
| `requests` | 视频元数据获取 | 是 |
| `yt-dlp` | YouTube 降级 + Bilibili 字幕 | 是 |
| `markdown` | Markdown → HTML 降级输出 | 否 |

## Skill 说明

详细的 AI 操作指令见 [技能说明/YouTube学习笔记生成器_Skill_v3.md](技能说明/YouTube学习笔记生成器_Skill_v3.md)，包含：
- 视频类型判断方法
- 多级内容获取降级策略
- 学习文档撰写规范
- HTML 输出规范
- 自审清单
