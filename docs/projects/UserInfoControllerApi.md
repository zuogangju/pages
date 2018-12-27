
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
└─pageNo|int|开始位置
└─pageSize|int|页数
└─search|string|模糊搜索内容
└─userId|string|用户id
└─startDate|string|开始时间(yyyy-MM-dd)
└─endDate|string|结束时间(yyyy-MM-dd)
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
	"code":0,
	"msg":"jhd6yi",
	"data":{
		"pageNo":103,
		"pageSize":274,
		"search":"9b30op",
		"userId":"iqg6wg",
		"startDate":"2018-12-27",
		"endDate":"2018-12-27",
		"instId":"of0kbq",
		"userId":"dkw6vp",
		"userName":"子轩.陆",
		"registCenter":[
			{
				"id":"sbvai6",
				"title":"xsw92c"
			}
		]
	}
}
```

