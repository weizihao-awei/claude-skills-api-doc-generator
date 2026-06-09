# API文档生成器 (API Doc Generator)

一个用于生成Java/Spring Boot后端项目API开发文档的Claude SKILL。

## 功能概述

按照中文模板格式，为Java/Spring Boot后端项目生成完整的API开发文档。**One interface = One document**，若用户需求涉及多个接口，会为每个接口分别生成独立文档。

## 核心特点

✅ **基于代码生成** - 从实际源码中提取信息，文档反映真实代码实现，不是理想设计  
✅ **中文模板** - 使用专业的中文API文档格式  
✅ **一接口一文档** - 每个接口独立成文，便于管理和查阅  
✅ **完整覆盖** - 包含接口描述和后端开发相关描述两大模块  
✅ **实用性强** - 包含实际SQL和Java代码，可直接用于开发  

## 使用方法

1. **触发方式**：
   - "生成接口文档"
   - "生成API文档"
   - "开发文档"
   - "后端文档"
   - "api docs"

2. **工作流程**：
   - 识别接口数量（多接口场景自动拆分）
   - 读取配置（输出目录、笔记属性）
   - 读取模板（`templates/api-doc-template.md`）
   - 读取项目源码（Controller、Service、Entity等）
   - 按照模板生成文档
   - 保存到指定目录
   - 自检并等待用户审核

## 文档结构

生成的文档包含两大模块：

### 第一模块：接口描述
1. 接口概述
2. 请求参数（含请求体参数、请求字段说明）
3. 响应格式（含响应字段说明）
4. 枚举定义（如适用）

### 第二模块：后端开发相关描述
1. 控制层与Service实现
2. 查询相关说明
3. 关键实现说明
4. 执行流程（含Mermaid流程图）
5. 数据库相关说明

## 核心原则

- **Document what exists, not what's planned** - 文档反映真实代码实现，不是理想设计
- **One interface = One document** - 永远一个接口对应一个文档

## 自检清单

生成文档后会自动检查：
- 笔记属性是否正确插入
- 两大模块是否完整
- 章节标题是否与模板一致
- 参数表格是否包含必要字段
- 代码示例是否完整
- 数据库表结构是否准确

## 安装方法

```bash
claude skills install https://github.com/weizihao-awei/claude-skills-api-doc-generator.git
```

## 贡献

欢迎提交Issue和Pull Request来改进这个SKILL！

## 许可证

MIT License