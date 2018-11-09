
# Description: 用户控制层
## 获取用户信息  todo 待测试
**URL:** null/m1/userinfo

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded



**Request-example:**
```
No request parameters are required.
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据
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
	"code":531,
	"msg":"d0vvq1",
	"data":{
		"instId":"ku3u14",
		"userId":"gy6vys",
		"userName":"航.潘",
		"agentInstId":"j3peio",
		"empnum":"06vam2",
		"emailbox":"mkr0g8",
		"ctttel":"o96s0u",
		"status":"ee018q",
		"description":"deja5m",
		"registCenter":[
			{
				"id":79,
				"title":"fw5iub"
			}
		]
	}
}
```

