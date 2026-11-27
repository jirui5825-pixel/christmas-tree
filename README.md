# 🎄 christmas-tree · v7.6

一棵会呼吸的 3D 粒子圣诞树。单页 HTML，纯 WebGL（three.js），没有后端、没有构建步骤、没有外部 CDN 依赖 —— 传上去就能看。

![预览](preview.jpg)

## 能做什么

- **20 000 颗粒子**组成的锥形树：外壳绿、螺旋金色彩带、金/红/冰蓝挂饰
- **顶星**会呼吸，地面有暖光；**飘雪**一直在下
- **拖动旋转**、**滚轮 / 双指缩放**，松手后缓慢自转
- **点击**任意位置，在树上撒一把星火
- **挂照片**：最多 14 张，自动做成拍立得，挂在树上
- **音乐**：WebAudio 现场合成《Jingle Bells》，不加载任何音频文件
- **写上名字**：`?to=小美` 打开就是「亲爱的 小美，愿这棵树替我陪你过冬」
- 手机 / 平板 / 桌面自适应，竖屏自动拉远镜头

## 本地打开

直接双击 `index.html` 就行（`vendor/` 要和它放在一起）。

> 需要浏览器支持 WebGL2。Chrome / Edge / Safari 新版本都可以；
> 如果一片黑，去 `chrome://settings/system` 打开「使用图形加速功能」。

## 放到 GitHub Pages

仓库已经按 Pages 的根目录结构排好：

```
index.html          # 页面本体
vendor/three.min.js # three.js（本地，不依赖 CDN）
.nojekyll           # 关掉 Jekyll，原样输出
```

推上去后：**Settings → Pages → Source: Deploy from a branch → main / (root) → Save**，
等一两分钟就能打开 `https://<你的用户名>.github.io/christmas-tree/`。

## 想改点什么

| 想改 | 去哪 |
| --- | --- |
| 树高 / 粗细 | `var H = 15;` / `var R = 6.2;` |
| 粒子数量（性能） | `N_SHELL` / `N_GARLAND` / `N_SNOW` |
| 顶部大字 | `<h1 class="title">Merry Christmas</h1>` |
| 副标题 | `<p class="sub" id="sub">…</p>`（写了名字会被 JS 覆盖） |
| 配色 | 搜 `setHSL`，改色相 / 饱和度 / 亮度 |

## 技术栈

three.js r151（UMD，本地）· 自定义 ShaderMaterial 点精灵 · AdditiveBlending ·
WebAudio 合成 · Canvas 生成贴图。零依赖、零构建。

## 许可

MIT。three.js 版权归 three.js authors（MIT）。
