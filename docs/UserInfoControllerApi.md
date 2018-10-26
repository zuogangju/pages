
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
	"code":144,
	"msg":"bdblbb",
	"data":{
		"instId":"z0as3q",
		"userId":"1093o4",
		"userName":"钰轩.洪",
		"agentInstId":"907k8c",
		"empnum":"jb6pj5",
		"emailbox":"lpgmns",
		"ctttel":"7s1zob",
		"status":"4mwdxr",
		"description":"cnjndl",
		"registCenter":[
			{
				"id":62,
				"title":"vdu988"
			}
		]
	}
}
```

