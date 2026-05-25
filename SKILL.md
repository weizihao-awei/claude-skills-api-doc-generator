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

### 2. 读取模板和代码

1. **先读模板**：使用绝对路径 `C:\Users\86158\.trae-cn\skills\claude-skills-api-doc-generator\templates\api-doc-template.md`
   - 必须完整读取模板文件内容
   - 理解模板的10个章节结构
   - 模板中 `[填写指南：...]` 标记是给AI的填写提示，生成文档时**必须用实际内容替换这些提示**，不得保留 `[填写指南：...]` 标记本身
2. **再读代码**：读取相关 Controller、Service、ServiceImpl、Entity 源文件

### 4. 生成并写入文件

- **强制要求**：生成的文档必须包含模板中的全部10个章节，不得遗漏、不得增删：

  1. 一、接口概述
  2. 二、请求参数
  3. 三、请求示例
  4. 四、响应参数
  5. 五、响应示例
  6. 六、错误码
  7. 七、注意事项
  8. 八、相关接口
  9. 九、代码实现参考
  10. 十、数据库表结构
- **章节标题必须与模板完全一致**（包括"一、二、三..."的编号格式）
- 每个章节下的内容必须根据实际代码填充，不能留空
- 代码块使用正确语法高亮（json、sql、java）
- 表格展示参数，对齐清晰
- 文件名用中文功能描述，如 `积分商品批量上下架接口文档.md`
- **必须使用Write工具创建文件**，不能只输出内容
- 写入目录：`C:\Users\86158\OneDrive\obsidian-vaults\xianganCompany开发仓库`
- 完整路径示例：`C:\Users\86158\OneDrive\obsidian-vaults\xianganCompany开发仓库\商户端附件分页列表接口文档.md`

### 4.5 生成后自检（强制执行）

生成文档后，必须逐项检查：

- [ ] 文档是否包含全部10个章节？
- [ ] 章节标题是否与模板一致（一、二、三...）？
- [ ] 是否清除了所有 `[填写指南：...]` 标记，替换为实际内容？
- [ ] 请求参数表格是否包含：参数名、类型、必填、描述、示例值？
- [ ] 响应参数表格是否包含：参数名、类型、描述？
- [ ] 是否包含JSON格式的请求/响应示例？
- [ ] 代码实现参考是否包含Controller/Service/Entity三段代码？
- [ ] 数据库表结构是否从Entity类反推？

**如有任何一项不符合，必须重新生成。**

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

## 模板章节填充指南

| 模板章节         | 数据来源               | 说明                                          |
| ---------------- | ---------------------- | --------------------------------------------- |
| 一、接口概述     | Controller注解         | @ApiOperation、@RequestMapping、@PreAuthorize |
| 二、请求参数     | Request类字段          | @ApiModelProperty注解                         |
| 三、请求示例     | 根据请求参数构造       | JSON或GET参数格式                             |
| 四、响应参数     | 返回对象字段           | CommonResult + 实际数据类型                   |
| 五、响应示例     | 根据响应结构构造       | 真实JSON示例                                  |
| 六、错误码       | 项目通用错误码         | 参考CommonResultCode                          |
| 七、注意事项     | 业务逻辑分析           | 权限、参数限制等                              |
| 八、相关接口     | 同一Controller其他方法 | 列出关联接口                                  |
| 九、代码实现参考 | 实际源码               | Controller/Service/Entity                     |
| 十、数据库表结构 | Entity类               | @TableName + 字段注解                         |

## 设计原则

- **基于代码**：字段类型、路径、方法名从源码获取，不编造
- **完整性**：覆盖所有需要的接口，不遗漏
- **实用性**：包含实际 SQL 和 Java 伪代码，可直接用于开发
- **规范性**：严格遵守模板格式
- **清晰性**：表格优先于段落，代码块优先于描述
