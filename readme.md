# HAR 解密查看器

一个纯前端的 HAR 文件浏览/解密工具。

## 快速开始

1. 用浏览器打开 `index.html`（直接双击，或 `python -m http.server` 启动本地服务器）
2. 点「选择 HAR」导入 HAR 文件
3. 点「⚙ 解密配置」查看算法和规则

## 添加解密算法

**永久添加**（推荐）——修改 `decoders.js`：

```javascript
window.HAR_DECODERS = {
  myDecrypt: {
    label: '我的解密',
    cdn: [],
    code: `function(bytes) {
      // bytes 是响应的原始字节（Uint8Array）
      // 这里写你的解密逻辑
      return JSON.parse(new TextDecoder().decode(bytes));
    }`
  },
};