---
name: api-doc-generator
description: >
  按照中文模板生成后端 API 开发文档。
  Use when user asks to "生成API文档", "生成接口文档", "开发文档", "后端文档", "api docs",
  "API documentation", or wants to document API endpoints before coding.
  Also triggered when user describes a new feature and says "先出文档" or "先写文档".
argument-hint: "[功能描述或需求说明]"
model: sonnet
---

# API 文档生成器

为 Java/Spring Boot 后端项目，按照中文模板格式生成 API 开发文档。

## 核心原则

**Document what exists, not what's planned.** 文档反映真实代码实现，不是理想设计。
生成前必须读取实际源码（Controller、Service、Entity），不能凭记忆或猜测填写。

## 工作流程

### 1. 确认项目

识别这是 Java/Spring Boot 项目，确认分层结构（controller/service/mapper/entity 包路径）。

### 2. 明确文档范围

如果用户未指定，先问要哪种文档：

| 选项 | 内容 | 用途 |
|---|---|---|
| 仅接口描述 | 第一模块（接口概述、请求/响应、枚举） | 可直接给前端 |
| 仅后端实现 | 第二模块（Controller/Service 代码、查询逻辑、表结构） | 给后端开发 |
| 完整文档（默认）| 两个模块都生成 | 前后端协作 |

### 3. 读取模板和代码

1. **先读模板**：`./templates/api-doc-template.md`，严格遵循其结构
2. **再读代码**：读取相关 Controller、Service、ServiceImpl、Entity 源文件
3. 模板中 `>` 标记的内容是 AI 提示词，不写入生成的文档

### 4. 生成文档

- 严格按模板结构，每个接口一个完整文档
- 代码块使用正确语法高亮（json、sql、java）
- 表格展示参数，对齐清晰
- 文件名用中文功能描述，如 `积分商品批量上下架接口文档.md`
- 写入目录：`C:\Users\86158\OneDrive\obsidian-vaults\xianganCompany开发仓库`

### 5. 交付前自检

- 功能覆盖：是否覆盖了用户提到的所有接口
- 格式正确：是否严格遵循模板结构，`>` 提示词是否已清除
- 代码准确：Controller/Service 路径、方法名、参数是否与源码一致
- 表结构完整：字段是否从实体类反推，与数据库对应

### 6. 等待审核

提交后提醒用户：
1. 请审核文档是否符合需求
2. 有修改要求请告知
3. **审核通过后**再开始写代码

## 设计原则

- **基于代码**：字段类型、路径、方法名从源码获取，不编造
- **完整性**：覆盖所有需要的接口，不遗漏
- **实用性**：包含实际 SQL 和 Java 伪代码，可直接用于开发
- **规范性**：严格遵守模板格式
- **清晰性**：表格优先于段落，代码块优先于描述
