# 音乐播放器 Web 应用设计文档

## 1. 项目概述

- **项目名称**：Aplus 音乐播放器
- **项目类型**：前后端分离的 Web 音乐播放器
- **核心功能**：本地 MP3 文件扫描、播放、进度拖拽、音量控制
- **输出文件**：`2.1/music-player.html`（前端）、`2.1/server.py`（后端）

## 2. 技术栈

- **前端**：100% 原生 HTML + CSS + JavaScript，无任何外部依赖
- **后端**：Python 3 标准库（`http.server`, `socketserver`, `os`, `json`）
- **音频**：HTML5 原生 `<audio>` 标签

## 3. 架构设计

### 3.1 文件结构
```
2.1/
├── music-player.html   # 前端单文件（内嵌CSS+JS）
├── server.py           # 后端单文件
└── *.mp3               # 音频文件（扫描同目录）
```

### 3.2 后端架构

**模块划分：**
- `scan_mp3_directory()` - 扫描同目录所有 .mp3 文件
- `parse_id3v1(path)` - 解析 ID3v1 标签（文件末尾 128 字节）
- `parse_id3v2(path)` - 解析 ID3v2 标签（文件开头）
- `get_mp3_metadata(path)` - 统一入口，返回 {title, artist, album}
- `MP3RequestHandler` - HTTP 请求处理类

**HTTP 路由：**
| 路由 | 方法 | 功能 |
|------|------|------|
| `/api/list` | GET | 返回 MP3 列表 + 元数据 |
| `/music/[filename].mp3` | GET | 流式返回 MP3 文件 |
| `/music-player.html` | GET | 返回 HTML 文件 |

**CORS 头**：所有响应添加 `Access-Control-Allow-Origin: *`

### 3.3 前端架构

**状态变量：**
```javascript
let isPlaying = false;        // 播放状态
let currentTrackIndex = 0;    // 当前曲目索引
let trackList = [];          // 曲目列表
let isDragging = false;       // 进度条拖拽状态
let volume = 0.8;             // 音量（默认80%）
```

**核心功能模块：**
1. 初始化 - DOMContentLoaded 后请求 `/api/list`
2. 播放控制 - 播放/暂停、上一曲/下一曲
3. 进度条 - 拖拽跳转（修改 audio.currentTime）
4. 音量控制 - 实时修改 audio.volume

## 4. ID3 元数据解析

### 4.1 ID3v2 解析
- 位于文件开头，以 `ID3` 标识开头
- 使用帧帧结构，解析 TIT2（标题）、TPE1（艺术家）、TALB（专辑）
- 编码：UTF-16（带 BOM）优先，否则 ISO-8859-1

### 4.2 ID3v1 解析
- 位于文件末尾 128 字节，以 `TAG` 标识开头
- 固定格式：标题30字节 + 艺术家30字节 + 专辑30字节
- 编码：GBK/ISO-8859-1

### 4.3 降级策略
```
ID3v2 存在 → 解析 ID3v2
ID3v2 不存在但 ID3v1 存在 → 解析 ID3v1
皆不存在 → title=文件名，artist/album="未知"
```

## 5. UI 像素规范（核心部分）

### 5.1 主卡片
- 尺寸：375px × 667px
- 背景色：`#1a1a22`
- 圆角：32px
- 内边距：上32px / 左右28px / 下40px

### 5.2 专辑封面
- 容器：240px × 240px，圆角20px
- 背景渐变：`linear-gradient(135deg, #7c3aed 0%, #ec4899 45%, #f97316 85%, #f59e0b 100%)`
- 中心唱片：外圆90px（#4c1616）+ 内圆28px（#0f172a）

### 5.3 进度条
- 宽度：`calc(100% - 100px)`
- 高度：6px
- 背景：`#33333b`，填充：`#8b5cf6`
- 滑块：20px 白色圆形

### 5.4 播放按钮
- 上一曲/下一曲：36px 线性图标
- 播放/暂停：70px 圆形，背景 `#8b5cf6`

## 6. 进度条拖拽实现（关键）

```javascript
// 事件绑定
progressContainer.addEventListener('mousedown', startDrag);
progressContainer.addEventListener('mousemove', onDrag);
progressContainer.addEventListener('mouseup', endDrag);
progressContainer.addEventListener('mouseleave', endDrag);

// 触摸兼容
progressContainer.addEventListener('touchstart', startDrag);
progressContainer.addEventListener('touchmove', onDrag);
progressContainer.addEventListener('touchend', endDrag);

function startDrag(e) {
    isDragging = true;
    updateProgressFromEvent(e);
}

function onDrag(e) {
    if (!isDragging) return;
    e.preventDefault();  // 阻止页面滚动
    updateProgressFromEvent(e);
}

function updateProgressFromEvent(e) {
    const rect = progressContainer.getBoundingClientRect();
    const x = (e.touches ? e.touches[0].clientX : e.clientX) - rect.left;
    const percent = Math.max(0, Math.min(1, x / rect.width));
    audio.currentTime = percent * audio.duration;
}
```

## 7. 验证清单

- [ ] 界面宽高比协调，无瘦高变形
- [ ] 进度条拖拽平滑跳转，不从头播放
- [ ] 上下曲切换自动跟随当前播放状态
- [ ] 音量条左右图标完整
- [ ] 歌名/专辑名动态渲染，无硬编码
- [ ] 无多余动画/阴影
- [ ] 前后端单文件，无第三方依赖