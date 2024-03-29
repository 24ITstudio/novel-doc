
# 小说相关API

## 热门小说榜单
GET
/hotnovel

### result

200

```JSON
[
    {
        "id"... // 见 “小说信息”
    },
    ...
]
```

## 分类小说
GET
/novel?tag&search=<分类>

### result
200

```JSON
[
    {
        "id"... // 见 “小说信息”
    },
    ...
]
```
或
```JSON
[]
```

## 小说信息
GET
/novel/<书id>

### result
如果 `<书id>` 有效：

200

```JSON
{
  "id": <int>,
  "name": <String>,
  "desc": <String>,
  "max_chapter": <int>,
}
```

否则：

404

```JSON
{"detail": "not found"}
```

## 小说某章节内容
GET
/novel/<书id>-<章节ord>

*NOTE*: 章节ord 从 1 开始 （而不是0）

### result
如果`<书id>`和`<章节ord>`都有效：

200

```JSON
{
  "content": <String>
}
```

如果`<章节ord>`非法 (小于1 或 大于该书最大章节)

404

```JSON
{
    "detail": "chapter not found"
}
```


如果`<书id>`非法

404

```JSON
{"detail": "not found"}
```

## 搜索小说
GET
/novel?search=<关键字>

### result

> 无论是否找到结果，状态码都为200

如果 找到结果

200

```JSON
[
    {
        "id"... // 见 “小说信息”
    }
    ...
]
```

无结果则返回空数组

200

```JSON
[]
```

> P.S. 前端对于用户的直接输入，应注意url编码，如使用[encodeURIComponent]( https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent)

