
# Description: 项目
## 项目列表查询
**URL:** http://{server}/m1/project/list

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
pageNo|int|开始位置|true
pageSize|int|页数|true
search|string|模糊搜索内容|false
startDate|string|开始时间(yyyy-MM-dd)|false
endDate|string|结束时间(yyyy-MM-dd)|false


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
└─pageNo|int|当前页
└─pageSize|int|每页的数量
└─total|number|总记录数
└─data|array|接口响应数据
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─userId|string|用户id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─instId|string|机构id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─isDelete|int|是否删除 1 删除  0 未删除
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─pjId|string|项目id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─pjNm|string|项目名称
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─pjDesc|string|项目描述
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─crtTs|string|创建时间
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─updTs|string|修改时间


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"qdlx97",
	"data":{
		"pageNo":410,
		"pageSize":400,
		"total":911,
		"data":[
			{
				"userId":"7i1z7c",
				"instId":"w9xjma",
				"isDelete":3,
				"pjId":"nzyljv",
				"pjNm":"tek5k4",
				"pjDesc":"cpw14y",
				"crtTs":"2018-12-27",
				"updTs":"2018-12-27"
			}
		]
	}
}
```

## 创建项目
**URL:** http://{server}/m1/project/save

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
userId|string|用户id|false
instId|string|机构id|false
isDelete|int|是否删除 1 删除  0 未删除|false
pjId|string|项目id|false
pjNm|string|项目名称|false
pjDesc|string|项目描述|false
crtTs|string|创建时间|false
updTs|string|修改时间|false


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


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"4npifx",
	"data":true
}
```

## 修改
**URL:** http://{server}/m1/project/update/{projectId}

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
userId|string|用户id|false
instId|string|机构id|false
isDelete|int|是否删除 1 删除  0 未删除|false
pjId|string|项目id|false
pjNm|string|项目名称|false
pjDesc|string|项目描述|false
crtTs|string|创建时间|false
updTs|string|修改时间|false


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


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"6vug7d",
	"data":true
}
```

## 删除项目
**URL:** http://{server}/m1/project/delete/{projectId}

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
projectId|string|项目id|true


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


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"9j7q8s",
	"data":true
}
```

