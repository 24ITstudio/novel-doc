
> 后端：返回的JSON

{"detail": "not found"}

## 热门小说榜单
GET
/hotnovel
```JSON
[
    {
        "id"... // 见 “小说信息”
    },
    ...
]
```


## 小说信息
GET
/novel/<书id>

```JSON
{
  "id": <int>,
  "name": <String>,
  "desc": <String>,
  "max_chapter": <int>,
}
```

## 小说某章节内容
GET
/novel/<书id>-<章节ord>

```JSON
{
  "content": <String>
}
```

NOTE: 章节ord 从 1 开始 （而不是0）



## 搜索小说
POST
/novel-search  POST-key: <关键字>

```JSON
[
    {
        "id"... // 见 “小说信息”
    }
    ...
]
```


