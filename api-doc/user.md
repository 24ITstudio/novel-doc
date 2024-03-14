

# 用户相关 API

*NOTE*: 所有 POST 等修改相关的URL都必须以 `/` 结尾

## 用户注册
POST
/register/
### data
```JSON
{"username": <String>, "password": <String>}
```
或
```JSON
{"username": <String>, "password": <String>, "favors":[<int>...]}
```

### result
201
```JSON
{...} // 暂未定
```

400
```JSON
{"username":["A user with that username already exists."]}
```

400
```JSON
{"password":["This field is required."]}
```

## 用户信息获取
/user/<用户id>/
GET, HEAD, OPTIONS
### result
200
```JSON
{"username": <String>, "favors": [<int>...]}
```

如果id非法/不存在
404
```JSON
{"detail":"Not found."}
```

## 用户令牌获取
/token-auth/
POST
### data
```JSON
{"username": <String>, "password": <String>}
```

### result
200
```JSON
{"token": <String>}
```

用户名或密码错误
400
```JSON
{"non_field_errors":["Unable to log in with provided credentials."]}
```

## 用户信息修改
/user/<用户id>/
PUT PATCH DELETE
> 需要Header包含 'Authorization: Token <token>

 
### result
200
```JSON
{...} // 暂未定
```


token不正确
401
```JSON
{"detail":"Invalid token."}
```
