# 🎄 christmas-tree · v7.6 gesture

一棵**用手控制的** 3D 粒子圣诞树：挥手转树、捏合缩放、握拳把它炸成星云，松手重新聚回来。

纯前端、单页 HTML —— Three.js 粒子 + 泛光后期 + MediaPipe 手部关键点，没有后端、没有构建步骤。

![预览](preview.jpg)

## 手部交互

点右下角 **✋ 手势** → 允许摄像头 → 把手放进左下角小窗里。

| 手势 | 效果 |
| --- | --- |
| 🖐 **张开手掌** | 左右移动 → 树跟着转；上下移动 → 抬升/压低机位 |
| 🤏 **拇指食指捏合** | 拉近 / 推远（捏得越紧越近） |
| ✊ **握拳** | 整棵树炸开成金色星云，同时放烟花 |
| ✌ **比 V** | 播放 / 暂停背景音乐 |

不想开摄像头？鼠标和触摸完全一样能用：拖动旋转、滚轮/双指缩放、点击撒星火。

> 摄像头画面**只在本机处理**，不上传、不录制、不保存。关掉页面就没了。

## 其它玩法

- **顶星**会呼吸，**雪**一直在下，**点击**任意位置撒一把星火 + 一小朵烟花
- **挂照片**：最多 14 张，自动做成拍立得挂在树上（同样只在本机）
- **音乐**：WebAudio 现场合成《Jingle Bells》，不加载任何音频文件
- **写上名字**：`?to=小美` 打开就是「亲爱的 小美，愿这棵树替我陪你过冬」
- 桌面 / 平板 / 手机三档自动取景

## 本地打开

```bash
npx serve .          # 或者任意静态服务器
```

浏览器直接双击 `index.html` 也能看（三维和鼠标交互都正常），
但**手势模式需要 http(s)**：`file://` 下浏览器禁止动态加载模型。

线上版本：**https://jirui5825-pixel.github.io/christmas-tree/**

## 目录

```
index.html                          # 页面本体（三维 + 手势 + 后期）
vendor/three.min.js                 # Three.js r151
vendor/mediapipe/vision_bundle.mjs  # MediaPipe Tasks Vision 0.10.3
vendor/mediapipe/wasm/*.wasm        # 手部识别的 wasm 运行时（8.3 MB）
vendor/mediapipe/models/hand_landmarker.task   # 手部 21 点模型（7.5 MB）
```

> 模型和 wasm 一共约 17 MB，**只有点「手势」时才会加载**，不影响首屏。

## 参考的开源项目

手势识别这套玩法来自社区里几个很棒的实现，本项目在它们的基础上重写了渲染与交互：

- [echoezy9527/christmas-tree-generated-by-gemini-3](https://github.com/echoezy9527/christmas-tree-generated-by-gemini-3)（Apache-2.0）— 「Gemini3 生成的手势控制 3D 粒子圣诞树」原作者版本，手势 + 烟花章节的思路来源
- [kK-2004/Ai-Gesture-Christmas-Tree](https://github.com/kK-2004/Ai-Gesture-Christmas-Tree)（MIT）— MediaPipe + Three.js 的手势照片树，配置化思路参考
- [Timo8848/gesture-Christmas_tree-3d_with_photo](https://github.com/Timo8848/gesture-Christmas_tree-3d_with_photo)（MIT）— 手势 + 照片点的工程结构参考
- [blackboxo/christmas-tree](https://github.com/blackboxo/christmas-tree) — 手势控制与视觉调性参考

## 技术栈

Three.js r151（UMD，本地）· 自定义 ShaderMaterial 点精灵 · 手写泛光后期（亮度提取 → 两次分离高斯 → 合成）·
2D Canvas 烟花层 · MediaPipe Tasks Vision（HandLandmarker，GPU/CPU 自动降级）· WebAudio 合成。

## 许可

本项目代码 MIT。第三方：
Three.js MIT（`vendor/LICENSE-three.txt`），MediaPipe Apache-2.0（`vendor/mediapipe/LICENSE`）。
