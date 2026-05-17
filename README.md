<div align="center">
  <img src="https://github.com/user-attachments/assets/57cb3034-9d29-40ee-9150-3475c87b8c23" width="800" alt="Mirage Player Logo" />
  <h1>Mirage Player</h1>
  <p><strong>液态玻璃 · 极致沉浸的音乐播放体验</strong></p>
  <p>一名高中牲开发的基于 Web 的现代音乐播放器，拥有液态玻璃美学、动态主题背景、CD 光效与实时音波可视化。</p>
  <p>
    <img src="https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white" />
    <img src="https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white" />
    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black" />
    <img src="https://img.shields.io/badge/license-MIT-blue" />
    <img src="https://img.shields.io/badge/version-1.0.0.0-blueviolet" />
  </p>
</div>

---

## 截图

![主界面](https://github.com/user-attachments/assets/3da54e7c-3593-4705-88e6-e2a2d120dd89) 

---

## 特性

- **21 套马卡龙主题配色** — 每首歌自动匹配最和谐的配色方案，手动随机切换一键换色
- **液态玻璃 CD** — 基于物理折射算法的高斯模糊 + 置换映射立体光效，鼠标悬浮晃动响应
- **实时音波可视化** — 柱状 / Apple 线条双样式，跟随主题色变化
- **歌词同步** — 自动从 MP3/FLAC 提取歌词，支持 LRC 文件匹配、手动导入、文本粘贴
- **封面提取** — 自动从音频文件提取封面，智能提取主色调并匹配 palette
- **播放列表管理** — 文件夹导入 / 拖放导入、专辑分组、单曲删除
- **底部悬浮控制栏** — 跟随侧栏状态动态收缩、液态玻璃晃动效果
- **响应式布局** — 侧栏可折叠收起，CD 区域自适应居中，移动端适配
- **CD 转速调节** — 设置中自由调整 0.2x-3x
- **SVG 涂鸦浮动背景** — 每套配色对应随机浮动 SVG 涂鸦，配合动态模糊圆斑
- **零依赖** — 纯 HTML + CSS + JavaScript，无需安装任何框架或库

---

## 快速体验

仓库中包含演示歌曲列表，可以直接导入体验：

1. 打开 Mirage Player
2. 点击「选择文件夹导入」
3. 选择仓库中的 `演示歌曲列表/` 文件夹
4. 即可试听演示歌曲 + 歌词同步 + 封面提取

---

## 下载安装

1. 前往 [Releases 页面](https://github.com/Mirage-BIN/MiragePlayer/releases/tag/MiragePlayer_v1.0)
2. 下载最新版本的 `MiragePlayer-Setup.exe` 安装程序
3. 运行安装程序，选择安装目录
4. 在安装目录中找到 `MiragePlayer.exe`，双击即可运行

## 如何获取自己的歌曲

如果你想使用自己的音乐，可以参考以下方式：

### 下载音乐

前往 [GD音乐台](https://music.gdstudio.xyz) 搜索并下载你喜欢的歌曲。

### 补全封面和歌词

下载 MusicTag 音乐标签编辑工具，可以一键获取歌曲的封面、歌词、专辑等信息。

> MusicTag 使用教程：[一键获取歌词、封面、专辑等信息，全能音乐信息标签采集软件](https://www.bilibili.com/video/BV1Kr4y1V7NU/?share_source=copy_web&vd_source=922be0f69bc3eefeb53e9eafd93d7ab0)

### 匹配规则

将 LRC 歌词文件与音乐文件放在**同一目录**并保持**同名**，Mirage Player 会自动匹配加载。

---

## 使用说明

| 操作 | 说明 |
|------|------|
| 点击 CD | 播放 / 暂停 |
| 拖放文件 | 拖放音频 / LRC 文件到播放列表区域 |
| 选择文件夹 | 点击「选择文件夹导入」或底部 + 按钮 |
| 侧栏收起 | 点击左侧栏顶部的 ◀ / 右侧歌词面板顶部的 ▶ |
| 切换主题 | 点击底栏左侧的调色盘按钮随机切换 |
| 设置 | 点击底栏左侧的齿轮按钮打开设置面板 |
| 删除歌曲 | 悬停歌曲行，点击右侧红色 ✕ |

---

## 主题配色

21 套预置马卡龙配色，覆盖红、橙、黄、绿、青、蓝、紫、粉、灰等色系。索引 #20（Teal）为默认启动配色。

配色通过 `MACARON_PALETTES` 数组定义，每套包含 5 个递进色值：
- `colors[0]` — 强调色（音波、Logo）
- `colors[1]` — 背景渐变色
- `colors[2-3]` — 模糊圆斑 & 涂鸦颜色
- `colors[4]` — 深色渐变端点

---

## 技术实现

| 模块 | 技术 |
|------|------|
| CD 光效 | CSS backdrop-filter + SVG filter（feDisplacementMap + feGaussianBlur） |
| 底部晃动 | 物理惯性模拟 + requestAnimationFrame |
| 配色切换 | CSS 变量 + 渐变过渡，transition: background 1.2s cubic-bezier(...) |
| 歌词解析 | 自定义 LRC 解析器，支持 [mm:ss.xx] 格式 |
| 封面提取 | 纯前端解析 MP3 ID3v2 与 FLAC 元数据 |
| 音频可视化 | Web Audio API AnalyserNode，requestAnimationFrame 绘制 Canvas |
| 响应布局 | ResizeObserver + updateLayout() 动态计算 |

---

## 版本规划

### v1.0.0.0（当前版本）
- 基础音乐播放功能
- 液态玻璃 CD 特效
- 主题配色系统
- 歌词同步
- 封面提取
- 播放列表管理
- 音波可视化

### 后续版本规划
- 音源联网搜索
- 在线音乐库
- 更多播放模式
- 自定义主题
- 更多语言支持
- 以及其他你想得到的功能...

---

## 开发者

一名高中牲课余自娱之作，持续更新中...

- **MirageBN** — [B站个人主页](https://space.bilibili.com/3546558473702169)
- **Mirage Team** — [B站团队主页](https://space.bilibili.com/3546938154683232)

### 赞助

如果这个项目让你感到愉悦，欢迎请我喝瑞幸茉莉花香拿铁

| 微信支付 | 支付宝 |
|:---:|:---:|
| ![微信支付](https://github.com/user-attachments/assets/fd9f540b-6fde-4680-8e0c-4d1a1893d939) | ![支付宝](https://github.com/user-attachments/assets/86bdf60c-604d-499d-b290-8d5541690a5d) |

---

## 许可

本项目仅供学习使用，禁止商用。

基于 MIT 许可证开源。
