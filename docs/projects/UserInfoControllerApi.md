
# Description: 用户控制类
## 获取用户信息接口
**URL:** http://{server}/userinfo

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded



**Request-example:**
```
No Request-example
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
└─instId|string|机构id
└─userId|string|用户id
└─userName|string|用户名称


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"ilsqkl",
	"data":{
		"instId":"y4uy6b",
		"userId":"ypvslm",
		"userName":"峻熙.魏"
	}
}
```

