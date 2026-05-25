# API 接口文档

## 一、接口概述

### 功能描述
[填写指南：描述这个接口的主要功能和使用场景]

### 接口地址
[填写指南：填写实际的接口路径，如 /api/your-endpoint]

### 请求方式
[填写指南：填写实际的HTTP方法，如 POST/GET/PUT/DELETE]

### 接口说明
[填写指南：详细说明接口的作用、使用限制、注意事项等]

## 二、请求参数

| 参数名 | 类型 | 必填 | 描述 | 示例值 |
|--------|------|------|------|--------|
| param1 | string | 是 | 参数1的描述 | test |
| param2 | number | 否 | 参数2的描述 | 123 |

## 三、请求示例

```json
{
  "param1": "test",
  "param2": 123
}
```

## 四、响应参数

| 参数名 | 类型 | 描述 |
|--------|------|------|
| code | number | 状态码 |
| message | string | 提示信息 |
| data | object | 响应数据 |

## 五、响应示例

```json
{
  "code": 200,
  "message": "操作成功",
  "data": {
    "result": "success"
  }
}
```

## 六、错误码

| 错误码 | 描述 |
|--------|------|
| 400 | 请求参数错误 |
| 401 | 未授权 |
| 403 | 禁止访问 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |

## 七、注意事项

[填写指南：列出使用该接口的注意事项、前置条件、后置处理等]

## 八、相关接口

[填写指南：列出与此接口相关的其他接口]

## 九、代码实现参考

### Controller 代码

```java
@RestController
@RequestMapping("/api/your-endpoint")
public class YourController {
    
    @PostMapping
    public ResponseEntity<Result> yourMethod(@RequestBody YourRequest request) {
        // 实现代码
    }
}
```

### Service 代码

```java
@Service
public class YourService {
    
    public Result yourMethod(YourRequest request) {
        // 实现代码
    }
}
```

### Entity 代码

```java
@Entity
@Table(name = "your_table")
public class YourEntity {
    
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    
    // 其他字段
}
```

## 十、数据库表结构

| 字段名 | 类型 | 描述 | 约束 |
|--------|------|------|------|
| id | bigint | 主键 | NOT NULL, AUTO_INCREMENT |
| param1 | varchar(255) | 参数1 |  |
| param2 | decimal(10,2) | 参数2 |  |

---
**模板使用说明**：模板中 `[填写指南：...]` 标记的内容是给AI的填写提示，生成文档时需用实际内容替换这些提示，不得保留 `[填写指南：...]` 标记本身。