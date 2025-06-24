# Hexo Mermaid Diagram Plugin

一个为 Hexo 博客系统提供 Mermaid 图表支持的插件，基于 iframe 的安全渲染方案。

## 特性

- 🔒 **安全渲染**: 使用 iframe 隔离用户内容，防止潜在的安全风险
- ⚡ **异步加载**: 图表异步渲染，不阻塞页面加载
- 🎨 **渐进增强**: 在不支持 JavaScript 的环境中显示原始代码
- 📱 **响应式**: 自适应不同屏幕尺寸
- 🎯 **简单易用**: 直接在 Markdown 中使用 mermaid 代码块

## 安装

```bash
npm install hexo-mermaid-diagram --save
```

## 使用方法

安装插件后，你可以在 Markdown 文件中直接使用 mermaid 代码块：

```markdown
​```mermaid
graph TD
    A[Hard] -->|Text| B(Round)
    B --> C{Decision}
    C -->|One| D[Result 1]
    C -->|Two| E[Result 2]
​```
```

## 配置

在 Hexo 的 `_config.yml` 中添加配置：

```yaml
mermaid_diagram:
  # Mermaid.js 版本
  version: "10.6.1"
  # 主题配置
  theme: "default"
  # 自定义 CSS 类名
  class_name: "mermaid-diagram"
  # 是否启用点击放大
  zoom: true
```

## 工作原理

本插件参考 GitHub 的实现方案：

1. **HTML 管道过滤器**: 扫描渲染后的 HTML，查找带有 `mermaid` 语言标识的代码块
2. **渐进式模板**: 替换为支持渐进增强的模板，在非 JavaScript 环境中显示原始代码
3. **iframe 注入**: 在支持 JavaScript 的环境中，注入指向渲染服务的 iframe
4. **安全隔离**: 用户内容在 iframe 中渲染，与主页面隔离

## 开发

```bash
# 克隆仓库
git clone https://github.com/your-username/hexo-mermaid-diagram.git
cd hexo-mermaid-diagram

# 安装依赖
npm install

# 链接到本地 Hexo 项目进行测试
npm link
cd /path/to/your/hexo/blog
npm link hexo-mermaid-diagram
```

## 许可证

MIT
