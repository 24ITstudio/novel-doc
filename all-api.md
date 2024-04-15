---
title: novel-backend
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - ruby: Ruby
  - python: Python
  - php: PHP
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
code_clipboard: true
highlight_theme: darkula
headingLevel: 2
generator: "@tarslib/widdershins v4.0.23"

---

# novel-backend

Base URLs:

# Authentication

* API Key (apikey-header-Authorization)
    - Parameter Name: **Authorization**, in: header. 

# novel

## GET novel-info-get

GET /novel/{id}

get novel infomation

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|id|path|integer| 是 |id of novel|

> 返回示例

> 200 Response

```json
{
  "id": 1,
  "name": "string",
  "desc": "string",
  "max_chapter": 0,
  "tag": "string"
}
```

> {id}非法

```json
{
  "details": "not found"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|{id}非法|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|true|none||none|
|» name|string|true|none||none|
|» desc|string|true|none||none|
|» max_chapter|integer|true|none||none|
|» tag|string|true|none||分类|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» details|string|true|none||none|

## POST novel-add

POST /novel/

add novel

requiring logined user

> Body 请求参数

```json
{
  "name": "string",
  "desc": "string",
  "max_chapter": 0,
  "tag": "string"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» name|body|string| 是 |none|
|» desc|body|string| 是 |none|
|» max_chapter|body|integer| 是 |none|
|» tag|body|string| 否 |none|

> 返回示例

> 200 Response

```json
{
  "id": 1,
  "name": "string",
  "desc": "string",
  "max_chapter": 0,
  "tag": "string"
}
```

> {id}非法

```json
{
  "details": "not found"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|{id}非法|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|true|none||none|
|» name|string|true|none||none|
|» desc|string|true|none||none|
|» max_chapter|integer|true|none||none|
|» tag|string|true|none||分类|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» details|string|true|none||none|

## POST chapter-add

POST /chapter/

add novel chapter

requiring logined user

> Body 请求参数

```json
{
  "name": "string",
  "desc": "string",
  "max_chapter": 0,
  "tag": "string"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» novel|body|integer| 是 |novel id|
|» chapter_ord|body|integer| 是 |none|
|» content|body|string| 否 |none|

> 返回示例

> 成功

```json
"{\r\n    \"id\": 1\r\n    \"novel\": 1,\r\n    \"chapter_ord\": 1,\r\n    \"content\": \"string\"\r\n}"
```

```json
{
  "novel": [
    "Invalid pk \"0\" - object does not exist."
  ]
}
```

```json
{
  "chapter_ord": [
    "chapter_ord must be a positive integer"
  ]
}
```

```json
{
  "non_field_errors": [
    "the chapter of given novel has alreadly exists"
  ]
}
```

```json
{
  "non_field_errors": [
    "the chapter order given exceeds novel's max_chapter"
  ]
}
```

> 400 Response

```json
{
  "novel": [
    "\"Invalid pk \\\"0\\\" - object does not exist.\""
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|novel id 有误|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|true|none||none|
|» novel|integer|true|none||none|
|» chapter_ord|integer|true|none||none|
|» content|string|true|none||none|

状态码 **400**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» novel|[string]|true|none||none|

## DELETE chapter-delete

DELETE /chapter/{id}

delete novel chapter with chapter id

requiring logined user

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|id|path|string| 是 |none|

> 返回示例

> 成功

```json
{
  "id": 1,
  "novel": 1,
  "chapter_ord": 1
}
```

```json
{
  "novel": [
    "Invalid pk \"0\" - object does not exist."
  ]
}
```

```json
{
  "chapter_ord": [
    "chapter_ord must be a positive integer"
  ]
}
```

```json
{
  "non_field_errors": [
    "the chapter of given novel has alreadly exists"
  ]
}
```

```json
{
  "non_field_errors": [
    "the chapter order given exceeds novel's max_chapter"
  ]
}
```

> 404 Response

```json
{
  "detail": "Not found."
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|记录不存在|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|true|none||none|
|» novel|integer|true|none||none|
|» chapter_ord|integer|true|none||none|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» detail|string|true|none||none|

## GET tags-search

GET /novel-tag

search novels by tags

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|search|query|string| 否 |none|

> 返回示例

> 成功

```json
[
  {
    "id": 1,
    "name": "n1",
    "desc": "Desc",
    "max_chapter": 1,
    "tag": "t"
  }
]
```

> {id}非法

```json
{
  "details": "not found"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|{id}非法|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|false|none||none|
|» name|string|false|none||none|
|» desc|string|false|none||none|
|» max_chapter|integer|false|none||none|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» details|string|true|none||none|

## GET name-search

GET /novel

search novels by name

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|search|query|string| 否 |none|

> 返回示例

> 成功

```json
[
  {
    "id": 1,
    "name": "n1",
    "desc": "Desc",
    "max_chapter": 1
  }
]
```

> {id}非法

```json
{
  "details": "not found"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|{id}非法|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|false|none||none|
|» name|string|false|none||none|
|» desc|string|false|none||none|
|» max_chapter|integer|false|none||none|
|» tag|string|false|none||none|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» details|string|true|none||none|

## GET novel-chapter-get

GET /novel/{book-id}-{chapter-ord}

小说某章节内容

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|book-id|path|integer| 是 |none|
|chapter-ord|path|integer| 是 |none|

> 返回示例

> 成功

```json
{
  "content": "Content"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» content|string|true|none||none|

## GET hotnovel-get

GET /hotnovel

热门小说榜单

> 返回示例

> 200 Response

```json
[
  {
    "id": 1,
    "name": "string",
    "desc": "string",
    "max_chapter": 1
  }
]
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|false|none||none|
|» name|string|false|none||none|
|» desc|string|false|none||none|
|» max_chapter|integer|false|none||none|

## GET tags-list

GET /novel-tag/

get all tags
获得所有标签

> 返回示例

> 成功

```json
[
  "",
  "t",
  "t1"
]
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

# user

## POST user-register

POST /register/

用户注册

> Body 请求参数

```json
{
  "username": "u6",
  "password": "u6"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» username|body|string| 是 |Can contain any unicode letters...|
|» password|body|string| 是 |none|

> 返回示例

> 201 Response

```json
{
  "id": 1
}
```

> 用户已存在

```json
{
  "username": [
    "A user with that username already exists."
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|成功|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|用户已存在|Inline|

### 返回数据结构

状态码 **201**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|integer|true|none||user id|

状态码 **400**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» username|[string]|true|none||none|

## GET user-info-get

GET /user/{user-id}/

用户信息获取

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|user-id|path|integer| 是 |none|

> 返回示例

> 成功

```json
{
  "username": "<String>",
  "favors": [
    1
  ]
}
```

> 404 Response

```json
{
  "detail": "Not found."
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|记录不存在|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» username|string|true|none||none|
|» favors|[integer]|true|none||none|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» detail|string|true|none||none|

## PATCH user-info-change

PATCH /user/{id}/

用户信息修改

> 需要Header包含 'Authorization: Token <token>

> Body 请求参数

```json
{
  "password": "u1"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|id|path|string| 是 |none|
|body|body|object| 否 |none|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

## DELETE user-delete

DELETE /user/{id}/

注销用户

> 需要Header包含 'Authorization: Token <token>

> Body 请求参数

```json
{
  "password": "u1"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|id|path|string| 是 |none|
|body|body|object| 否 |none|

> 返回示例

> 200 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|

### 返回数据结构

## POST login-token-get

POST /token-auth/

用户令牌获取

> Body 请求参数

```json
{
  "username": "u6",
  "password": "u6"
}
```

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|body|body|object| 否 |none|
|» username|body|string| 是 |none|
|» password|body|string| 是 |none|

> 返回示例

> 成功

```json
{
  "token": "12f49d290f4817b6eedb8b46dbcbd0458fec8472"
}
```

> 验证失败

```json
{
  "non_field_errors": [
    "Unable to log in with provided credentials."
  ]
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|验证失败|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» token|string|true|none||none|

状态码 **400**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» non_field_errors|[string]|true|none||none|

## POST favor-add

POST /favor/{novel-id}/

添加收藏

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|novel-id|path|integer| 是 |none|

> 返回示例

> 201 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|成功|Inline|

### 返回数据结构

## DELETE favor-delete

DELETE /favor/{novel-id}/

添加收藏

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|novel-id|path|integer| 是 |none|

> 返回示例

> 204 Response

```json
{}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|删除成功|Inline|

### 返回数据结构

## GET user-id-get

GET /user-id/{username}/

通过username获得user的id

### 请求参数

|名称|位置|类型|必选|说明|
|---|---|---|---|---|
|username|path|string| 是 |none|

> 返回示例

> 200 Response

```json
{
  "id": "string"
}
```

### 返回结果

|状态码|状态码含义|说明|数据模型|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|成功|Inline|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|该用户名不存在|Inline|

### 返回数据结构

状态码 **200**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» id|string|true|none||user id|

状态码 **404**

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|» details|string|true|none||none|

# 数据模型

<h2 id="tocS_Novel">Novel</h2>

<a id="schemanovel"></a>
<a id="schema_Novel"></a>
<a id="tocSnovel"></a>
<a id="tocsnovel"></a>

```json
{
  "id": 0,
  "name": "string",
  "desc": "string",
  "max_chapter": 0,
  "tag": "string"
}

```

### 属性

|名称|类型|必选|约束|中文名|说明|
|---|---|---|---|---|---|
|id|integer|true|none||none|
|name|string|true|none||none|
|desc|string|true|none||none|
|max_chapter|integer|true|none||none|
|tag|string|false|none||none|

