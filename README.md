# Object Detection

<div align="center">

**基于 TensorFlow.js 的实时目标检测** — 浏览器端 YOLOv8 目标检测应用

[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow.svg)](https://developer.mozilla.org/)
[![TensorFlow.js](https://img.shields.io/badge/TensorFlow.js-4.x-ff6f00.svg)](https://www.tensorflow.org/js)
[![YOLOv8](https://img.shields.io/badge/YOLOv8-Ultralytics-00FFFF.svg)](https://github.com/ultralytics/ultralytics)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

</div>

---

## Features

- **实时检测** — 浏览器端实时目标检测，无需服务器
- **多版本支持** — 支持 YOLOv8/v9/v10/v11 多个版本
- **多语言界面** — 支持中文/英文切换
- **移动优化** — 针对手机端优化，支持摄像头检测
- **离线运行** — 模型本地加载，支持离线使用

## Project Structure

```
object-detection/
├── index.html               # 主应用页面
├── index_v2.html            # 版本 2
├── index_v3.html            # 版本 3
├── index_v4.html            # 版本 4
├── index_v5.html            # 版本 5
├── index_v6.html            # 版本 6
├── index_v7.html            # 版本 7
├── index_v8_yolo.html       # YOLOv8 版本
├── index_v9_yolo.html       # YOLOv9 版本
├── index_v10_cn.html        # YOLOv10 中文版
├── index_v10_yolo.html      # YOLOv10 英文版
├── index_v11_final.html     # YOLOv11 最终版
├── index_v11_final_TTS.html # YOLOv11 + 语音版
├── yolov8n_web_model/       # YOLOv8n Web 模型
│   ├── model.json           # 模型配置
│   ├── group1-shard1of1.bin # 模型权重
│   └── ...
├── LICENSE                  # MIT 许可证
└── README.md                # 项目说明文档
```

## Quick Start

### Prerequisites

- 现代浏览器 (Chrome, Firefox, Safari, Edge)
- 摄像头权限 (可选，用于实时检测)

### Run

```bash
# 方法 1: 直接打开 HTML 文件
# 双击 index.html 或在浏览器中打开

# 方法 2: 使用本地服务器 (推荐)
python -m http.server 8000
# 然后在浏览器中访问 http://localhost:8000

# 方法 3: 使用 Node.js
npx serve .
```

### 使用说明

1. **选择检测模式**:
   - 图片检测: 上传图片进行检测
   - 摄像头检测: 使用摄像头实时检测

2. **选择模型版本**:
   - YOLOv8: 平衡速度和精度
   - YOLOv9: 更高精度
   - YOLOv10: 最新架构
   - YOLOv11: 最新版本

3. **调整参数**:
   - 置信度阈值: 控制检测灵敏度
   - NMS 阈值: 控制重叠框过滤

## Technical Architecture

### 模型架构

```
输入图像 (640x640)
    ↓
YOLOv8 Backbone (CSPDarknet)
    ↓
Neck (PANet + FPN)
    ↓
Head (Decoupled Head)
    ↓
检测结果 (类别 + 置信度 + 边界框)
```

### TensorFlow.js 集成

```javascript
// 加载模型
const model = await tf.loadGraphModel('yolov8n_web_model/model.json');

// 预处理图像
const input = tf.browser.fromPixels(image)
  .resizeBilinear([640, 640])
  .div(255.0)
  .expandDims(0);

// 推理
const predictions = model.predict(input);

// 后处理
const detections = postProcess(predictions);
```

## Model Performance

| 模型 | 精度 (mAP) | 速度 (FPS) | 模型大小 |
|:--|:--:|:--:|:--:|
| YOLOv8n | 37.3 | 45 | 6.2 MB |
| YOLOv8s | 44.9 | 35 | 21.5 MB |
| YOLOv9t | 38.3 | 42 | 5.8 MB |
| YOLOv10n | 39.5 | 48 | 5.4 MB |
| YOLOv11n | 40.2 | 50 | 5.6 MB |

## Supported Classes

支持 COCO 数据集的 80 个类别，包括：

- 人物: person
- 交通工具: car, truck, bus, bicycle, motorcycle
- 动物: cat, dog, bird, horse
- 日用品: cup, book, cell phone
- 等等...

## Browser Compatibility

| 浏览器 | 版本 | 支持状态 |
|:--|:--:|:--:|
| Chrome | 90+ | 完全支持 |
| Firefox | 88+ | 完全支持 |
| Safari | 14+ | 完全支持 |
| Edge | 90+ | 完全支持 |

## License

[MIT](LICENSE)
