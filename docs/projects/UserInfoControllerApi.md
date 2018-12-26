
# Description: 用户控制类
## 获取用户信息接口
**URL:** null/userinfo

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded



**Request-example:**
```
No Request-example
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
└─registCenter|array|注册中心
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─id|string|注册中心名称
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─title|string|注册中心值


**Response-example:**
```
{
	"succ":true,
	"code":227,
	"msg":"5jjq17",
	"data":{
		"instId":"13m5a2",
		"userId":"kngksv",
		"userName":"博文.吕",
		"registCenter":[
			{
				"id":"l1zjx1",
				"title":"hn4h1u"
			}
		]
	}
}
```

