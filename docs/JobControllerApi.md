
# Description: M1控制层
## 根据注册中心获取容器列表 //TODO 待实现
**URL:** http://{server}/m1/regist/center/container

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
registId|string|注册中心id|false


**Request-example:**
```
No Parameter
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
└─id|string|id
└─title|string|容器


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"v5e32m",
	"data":[
		{
			"id":"q5r9ai",
			"title":"rtpkoh"
		}
	]
}
```

## 元数据列表查询(支持模糊查询) //TODO 待测试
**URL:** http://{server}/m1/metadata/list

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
tableName|string|表名称(支持模糊查询)|true
pageNo|int|   页码|true
pageSize|int| 页数|true


**Request-example:**
```
No Parameter
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
└─tableName|string|表名称
└─fields|map|字段信息{"id":"string","name":"string","type":"string"}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─any object|object|any object.
└─filePath|string|存储路径信息


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"t8gy02",
	"data":[
		{
			"tableName":"笑愚.丁",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"inj0zd"
		}
	]
}
```

## 获取数据源 //TODO 待实现
**URL:** http://{server}/m1/datasource/list

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
└─id|string|数据库id
└─title|string|数据库名称


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"134phf",
	"data":[
		{
			"id":"bix4kn",
			"title":"ydvute"
		}
	]
}
```

## 重新运行调度 //TODO 待实现
**URL:** http://{server}/m1/job/restart

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
jobId|string|任务id|true


**Request-example:**
```
No Parameter
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
	"msg":"78dbtl",
	"data":"q2bhyv"
}
```

## 停止调度 //TODO 待实现
**URL:** http://{server}/m1/job/stop

**Type:** POST

**Content-Type:** application/json; charset=utf-8


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
name|string|任务名称|false
taskId|string|taskId|false
centerId|string|注册中心id|false
containerId|string|容器id|false
sql|string|sql|false
fileType|string|文件类型|false
sqlName|string|sql名称|false


**Request-example:**
```
{
	"name":"笑愚.丁",
	"taskId":"81i6ug",
	"centerId":"uaoiry",
	"containerId":"uyxdmc",
	"sql":"xopxvm",
	"fileType":"vvtwgm",
	"sqlName":"笑愚.丁"
}
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
	"msg":"djwtir",
	"data":579
}
```

## 保存(保存调度信息)/启用调度信息(周期调度)/执行调度(立即执行) //TODO 待测试
**URL:** http://{server}/m1/job/save

**Type:** POST

**Content-Type:** application/json; charset=utf-8


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
jobId|string|任务时间|true
name|string|名称|false
execType|int|执行类型 0:保存;1:启动;2:启用调度|false
centerId|string|注册中心id|false
containerId|string|容器id|false
isOutFile|int|是否输出文件|false
isSch|int|是否配置调度|false
sch|object|调度信息|false
└─schType|string|调度类型|false
└─schDate|string|调度日期|false
└─schTime|string|调度时间|false
└─isDataSource|int|是否配置数据源|false
└─schCycleNum|string|周期时间|false
└─dataSource|array|数据源信息|false
sqlInfo|array|sql信息|false
└─sql|string|sql内容|false
└─fileType|string|文件类型|false
└─sqlName|string|sql名称|false
fileName|string|输出文件名称|false


**Request-example:**
```
{
	"jobId":"bn4wy8",
	"name":"笑愚.丁",
	"execType":418,
	"centerId":"all3m2",
	"containerId":"9ql3oj",
	"isOutFile":740,
	"isSch":92,
	"sch":{
		"schType":"9bk5wm",
		"schDate":"2018-10-25",
		"schTime":"2018-10-25 14:27:55",
		"isDataSource":191,
		"schCycleNum":"sc34q9",
		"dataSource":[
			""w3ykdg""
		]
	},
	"sqlInfo":[
		{
			"sql":"xk66q1",
			"fileType":"kpr8k6",
			"sqlName":"笑愚.丁"
		}
	],
	"fileName":"笑愚.丁"
}
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
└─sceneId|string|场景标识
└─jobId|int|任务Id
└─jobDesc|string|任务描述
└─jobType|string|任务类型
└─job|string|任务文件路径
└─cond|string|调度信息
└─parameter|string|其他参数
└─info|string|其他信息
└─retry|int|重试次数
└─timeout|int|超时时间
└─taskId|string|taskId
└─status|string|状态信息


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"kbrc7j",
	"data":[
		{
			"sceneId":"atx41t",
			"jobId":510,
			"jobDesc":"kziqkp",
			"jobType":"jygd32",
			"job":"irbozi",
			"cond":"kfqkgj",
			"parameter":"qn7q36",
			"info":"xhc9ru",
			"retry":142,
			"timeout":427,
			"taskId":"kvfnj0",
			"status":"423vxl"
		}
	]
}
```

## 获取任务列表 //TODO 待测试
**URL:** http://{server}/m1/job/list

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
centerId|string|注册中心id|false
containerId|string|容器id|false
startDate|string|任务开始时间|false
endDate|string|任务结束时间|false
status|string|状态|false
cycle|string|周期|false
name|string|名称|false
pageNo|int|页码|false
pageSize|int|页数|false


**Request-example:**
```
No Parameter
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
└─pageNo|int|No comments found.
└─pageSize|int|No comments found.
└─total|number|No comments found.
└─data|array|接口响应数据
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobId|string|任务Id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobName|string|任务名称
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobStatus|string|任务状态
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─schCycleNum|string|周期时间
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─condition|string|调度信息
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobStartDateTime|string|任务开始时间
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobEndDateTime|string|任务结束时间
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─schType|string|周期


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"id7fja",
	"data":{
		"pageNo":955,
		"pageSize":681,
		"total":13,
		"data":[
			{
				"jobId":"m04fit",
				"jobName":"笑愚.丁",
				"jobStatus":"a463fz",
				"schCycleNum":"pnpkju",
				"condition":"9yf6t2",
				"jobStartDateTime":"2018-10-25",
				"jobEndDateTime":"2018-10-25",
				"schType":"0pv2rf"
			}
		]
	}
}
```

## 下载结果 //TODO 待实现
**URL:** http://{server}/m1/job/downloadResult

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
taskId|int|taskId|true


**Request-example:**
```
No Parameter
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
	"msg":"kl00pd",
	"data":309
}
```

## 配置调度 //TODO 待测试
**URL:** http://{server}/m1/job/update/{jobId}

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
jobId|string|任务时间|true
name|string|名称|false
execType|int|执行类型 0:保存;1:启动;2:启用调度|false
centerId|string|注册中心id|false
containerId|string|容器id|false
isOutFile|int|是否输出文件|false
isSch|int|是否配置调度|false
sch|object|调度信息|false
└─schType|string|调度类型|false
└─schDate|string|调度日期|false
└─schTime|string|调度时间|false
└─isDataSource|int|是否配置数据源|false
└─schCycleNum|string|周期时间|false
└─dataSource|array|数据源信息|false
sqlInfo|array|sql信息|false
└─sql|string|sql内容|false
└─fileType|string|文件类型|false
└─sqlName|string|sql名称|false
fileName|string|输出文件名称|false


**Request-example:**
```
No Parameter
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
└─sceneId|string|场景标识
└─jobId|int|任务Id
└─jobDesc|string|任务描述
└─jobType|string|任务类型
└─job|string|任务文件路径
└─cond|string|调度信息
└─parameter|string|其他参数
└─info|string|其他信息
└─retry|int|重试次数
└─timeout|int|超时时间
└─taskId|string|taskId
└─status|string|状态信息


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"zx32d6",
	"data":[
		{
			"sceneId":"nf9jo6",
			"jobId":926,
			"jobDesc":"hglm1b",
			"jobType":"ahk17e",
			"job":"slixwn",
			"cond":"jpgeyf",
			"parameter":"jx59kh",
			"info":"vjc5dk",
			"retry":196,
			"timeout":727,
			"taskId":"m2bj2k",
			"status":"tnfuab"
		}
	]
}
```

## 查看日志 //TODO 待实现
**URL:** http://{server}/m1/job/log

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
taskId|int|taskId|true


**Request-example:**
```
No Parameter
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
	"msg":"bh9wes",
	"data":"wpp3am"
}
```

