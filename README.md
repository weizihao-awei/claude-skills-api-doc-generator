# API文档生成器 (API Doc Generator)

一个用于生成Java/Spring Boot后端项目API开发文档的Claude SKILL。

## 功能概述

按照中文模板格式，为Java/Spring Boot后端项目生成完整的API开发文档，包括：
- 接口概述
- 请求参数和示例
- 响应参数和示例  
- 错误码说明
- 代码实现参考
- 数据库表结构

## 核心特点

✅ **基于代码生成** - 从实际源码中提取信息，确保文档准确性  
✅ **中文模板** - 使用专业的中文API文档格式  
✅ **完整覆盖** - 包含前后端需要的所有文档部分  
✅ **实用性强** - 包含实际SQL和Java伪代码，可直接用于开发  

## 使用方法

1. **触发方式**：
   - "生成API文档"
   - "生成接口文档" 
   - "开发文档"
   - "后端文档"
   - "api docs"
   - "API documentation"
   - "先出文档" 或 "先写文档"

2. **工作流程**：
   - 识别Java/Spring Boot项目结构
   - 确认文档生成范围（仅接口描述/仅后端实现/完整文档）
   - 读取Controller、Service、Entity源码
   - 按照模板生成文档
   - 保存到指定目录

## 文档结构

生成的文档包含以下部分：
1. 接口概述
2. 请求参数
3. 请求示例
4. 响应参数
5. 响应示例
6. 错误码
7. 注意事项
8. 相关接口
9. 代码实现参考
10. 数据库表结构

## 安装方法

```bash
claude skills install https://github.com/weizihao-awei/claude-skills-api-doc-generator.git
```

## 贡献

欢迎提交Issue和Pull Request来改进这个SKILL！

## 许可证

MIT License