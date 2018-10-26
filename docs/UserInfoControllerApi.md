
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
	"msg":"asrn9g",
	"data":{
		"instId":"6vcpyk",
		"userId":"66vnxr",
		"userName":"振家.冯",
		"agentInstId":"nxsoe9",
		"empnum":"581k2r",
		"emailbox":"6xxgub",
		"ctttel":"cbt07z",
		"status":"6fpsf6",
		"description":"l7030j",
		"registCenter":[
			{
				"id":375,
				"title":"9ps7o6"
			}
		]
	}
}
```

