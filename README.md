# Object Detection

基于 YOLO 的目标检测 Web 应用

## 功能特性

- 🎯 实时目标检测
- 🌐 Web 界面交互
- 📸 支持图片和视频检测
- 🚀 基于 TensorFlow.js 的浏览器端推理

## 技术栈

- **前端**: HTML5, CSS3, JavaScript
- **模型**: YOLOv8 (TensorFlow.js 格式)
- **框架**: TensorFlow.js

## 项目结构

```
object-detection/
├── index.html              # 主页面 (最新版本)
├── index_v10_cn.html       # v10 中文版
├── index_v10_yolo.html     # v10 YOLO 版
├── index_v11_final.html    # v11 最终版
├── index_v11_final_TTS.html # v11 TTS 版本
├── index_v2.html           # v2 版本
├── index_v3.html           # v3 版本
├── index_v4.html           # v4 版本
├── index_v5.html           # v5 版本
├── index_v6.html           # v6 版本
├── index_v7.html           # v7 版本
├── index_v8_yolo.html      # v8 YOLO 版
├── index_v9_yolo.html      # v9 YOLO 版
├── yolov8n_web_model/      # YOLOv8n 模型文件
└── LICENSE                 # MIT 许可证
```

## 快速开始

### 本地运行

1. 克隆仓库
```bash
git clone https://github.com/beahanbarry291994-cmd/object-detection.git
cd object-detection
```

2. 启动本地服务器
```bash
# 使用 Python
python -m http.server 8000

# 或使用 Node.js
npx serve .
```

3. 打开浏览器访问 `http://localhost:8000`

### 使用方法

1. 打开页面后，允许摄像头权限或上传图片
2. 系统会自动进行目标检测
3. 检测结果会实时显示在画面上

## 版本说明

- **v11**: 最终版本，功能完善
- **v10**: 添加中文支持
- **v9**: YOLO 模型集成
- **v2-v8**: 历史版本迭代

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件