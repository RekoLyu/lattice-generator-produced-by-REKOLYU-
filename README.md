# Lattice STL Generator

一个无需安装、无需服务器计算的参数化晶格 STL 生成器。所有模型均在访问者的浏览器中本地生成，实验参数和 STL 文件不会上传到服务器。

## 支持的晶格

- **Simple Cubic (SC)**：方形截面杆件；使用净空隙尺寸和方杆边长定义。
- **BCC**：每个体心连接单胞的八个角点；使用圆形截面杆件。
- **BCCZ**：BCC 斜杆加 Z 方向圆形竖杆。

尺寸输入单位统一为 **mm**。例如：

- \`0.1 mm = 100 μm\`
- \`0.02 mm = 20 μm\`

连续尺寸不设置人为工艺下限，只要求输入值大于 0。

## 本地使用

双击 \`index.html\`，使用 Chrome 或 Edge 打开。设置参数并更新预览后，点击“生成 STL 下载文件”，再点击页面生成的蓝色下载链接。

## 发布到 GitHub Pages

1. 在 GitHub 创建一个名为 \`lattice-generator\` 的公开仓库。
2. 将本项目中的 \`index.html\`、\`README.md\` 和 \`LICENSE\` 上传到仓库根目录。
3. 打开仓库的 **Settings → Pages**。
4. 在 **Build and deployment** 中选择 **Deploy from a branch**。
5. Branch 选择 \`main\`，目录选择 \`/(root)\`，然后保存。
6. 等待 GitHub 完成部署。网页地址通常为：

   \`https://你的GitHub用户名.github.io/lattice-generator/\`

## 后续更新

用新版 \`index.html\` 替换仓库根目录中的旧文件并提交。GitHub Pages 会自动重新发布，网页地址保持不变。若浏览器仍显示旧版，可按 \`Ctrl + F5\` 强制刷新。

## 几何说明

### Simple Cubic

输入的 \`Pore opening\` 是相邻方杆内表面之间的净空隙。若单个方向有 N 个空隙、净空隙为 P、方杆边长为 W，总尺寸为：

\`L = N × P + (N + 1) × W\`

SC 导出时保留整个方杆晶格并集的外表面。

### BCC / BCCZ

显示的尺寸是最外层角节点中心之间的名义跨度。圆杆截面可能在边界节点附近略微超出该跨度。BCC 和 BCCZ 的 STL 由相交的封闭圆柱组成，常用切片软件通常能够自动合并；如用于严格有限元分析，建议在 CAD/网格软件中执行布尔并集和网格检查。

## 浏览器

推荐使用最新版 Chrome 或 Edge。网页不依赖外部 JavaScript 库，可离线运行。

## License

MIT License。详见 \`LICENSE\`。
