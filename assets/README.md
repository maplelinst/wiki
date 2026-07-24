# 图片与资源

本目录存放知识库中所有 Markdown 文档引用的图片、图表和附件。

## 目录结构

```
assets/
├── images/          # 截图、照片、插图
│   ├── screenshots/
│   ├── learning/
│   ├── work/
│   └── reference/
├── diagrams/        # 架构图、流程图
├── attachments/     # PDF、文档等附件
└── thumbnails/      # 缩略图
```

## 引用方式

在 Markdown 文档中使用相对路径引用：

```markdown
![描述](../assets/images/work/screenshot-name.png)
```

## 元数据管理

所有图片的元数据记录在 `_config/metadata.json` 中，包括来源、许可证、关联文档等信息。
