
# Description: 用户控制层
## 获取用户信息  todo 待测试
**URL:** http://{server}/m1/userinfo

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded



**Request-example:**
```
No request parameters are required.
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
└─agentInstId|string|代理机构id
└─empnum|string|No comments found.
└─emailbox|string|No comments found.
└─ctttel|string|No comments found.
└─status|string|状态
└─description|string|描述
└─registCenter|array|注册中心
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─id|int|注册中心Id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─title|string|注册中心名称


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"3h4ncf",
	"data":{
		"instId":"2gfglk",
		"userId":"ibnea4",
		"userName":"峻熙.赵",
		"agentInstId":"clqqpj",
		"empnum":"mzzoo0",
		"emailbox":"so7e9h",
		"ctttel":"q5jqw5",
		"status":"3e9vw9",
		"description":"aifejf",
		"registCenter":[
			{
				"id":321,
				"title":"1muxkk"
			}
		]
	}
}
```

