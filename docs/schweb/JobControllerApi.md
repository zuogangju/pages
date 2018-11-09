
# Description: 任务接口
## 根据注册中心获取容器列表 //TODO 待实现
**URL:** null/m1/regist/center/container

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
registId|string|注册中心id|true


**Request-example:**
```
No Request-example111
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据
└─id|string|id
└─title|string|容器


**Response-example:**
```
{
	"succ":true,
	"code":931,
	"msg":"hsxsi9",
	"data":[
		{
			"id":"ke7bnq",
			"title":"ygqf8e"
		}
	]
}
```

## 元数据列表查询(支持模糊查询) //TODO 待测试
**URL:** null/m1/metadata/list

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
tableName|string|表名称(支持模糊查询)|false
pageNo|int|   页码|true
pageSize|int| 页数|true


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
└─tableName|string|表名称
└─fields|map|字段信息{"id":"string","name":"string","type":"string"}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─any object|object|any object.
└─filePath|string|存储路径信息


**Response-example:**
```
{
	"succ":true,
	"code":702,
	"msg":"1thnrh",
	"data":[
		{
			"tableName":"航.潘",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"dw6cm2"
		}
	]
}
```

## 获取数据源 //TODO 待测试
**URL:** null/m1/datasource/list

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
└─id|string|数据库id
└─title|string|数据库名称


**Response-example:**
```
{
	"succ":true,
	"code":405,
	"msg":"69dxle",
	"data":[
		{
			"id":"ssutg6",
			"title":"yigfx1"
		}
	]
}
```

## 重新运行调度 //TODO 待实现
**URL:** null/m1/job/restart

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
jobId|string|任务id|true


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


**Response-example:**
```
{
	"succ":true,
	"code":435,
	"msg":"wguowg",
	"data":"nrkgg5"
}
```

## 停止调度 //TODO 待实现
**URL:** null/m1/job/stop

**Type:** POST

**Content-Type:** application/json; charset=utf-8


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
name|string|任务名称|true
taskId|string|taskId|false
centerId|string|注册中心id|true
containerId|string|容器id|true
sql|string|sql|false
fileType|string|文件类型|false
sqlName|string|sql名称|false


**Request-example:**
```
{
	"name":"航.潘",
	"taskId":"dpj15a",
	"centerId":"1tyic2",
	"containerId":"7oh852",
	"sql":"ndpzdz",
	"fileType":"5zg14e",
	"sqlName":"航.潘"
}
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":993,
	"msg":"rc4e67",
	"data":454
}
```

## 保存(保存调度信息)/启用调度信息(周期调度)/执行调度(立即执行) //TODO 待测试
**URL:** null/m1/job/save

**Type:** POST

**Content-Type:** application/json; charset=utf-8


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
jobId|string|任务id|false
name|string|名称|true
execType|int|执行类型 0:保存调度 1:启用调度 2:执行任务调度(立即执行)|true
execFilePath|string|执行文件路径(绝对路径)|false
centerId|string|注册中心id|true
containerId|string|容器id|true
isOutFile|int|是否输出文件 (1:是 0:否)|true
isSch|int|是否配置调度(1:是 0:否)|true
sch|object|调度信息|false
└─schType|string|调度类型(number:次,day:日,week:周,month:月)|false
└─schDate|string|调度日期(yyyy-MM-dd)|false
└─schTime|string|调度时间(范围值 3-23)|false
└─isDataSource|int|是否配置数据源(1:有;0:否,isDataSource=1需配置dataSource,反之不需要配置)|true
└─schCycleNum|string|周期时间(例:周2-周日执行,范围 2-7)|false
└─dataSource|array|数据源信息|false
sqlInfo|array|sql信息|false
└─sql|string|sql内容|false
└─fileType|string|文件类型(如果isOutFile=0 则fileType可以传null)|false
└─sqlName|string|sql名称|false
└─filePath|string|sql文件路径|false
fileName|string|输出文件名称(如果isOutFile=0 则fileName可以传null)|false


**Request-example:**
```
{
	"jobId":"07ic19",
	"name":"航.潘",
	"execType":109,
	"execFilePath":"lnq5l3",
	"centerId":"3mt0o5",
	"containerId":"ahfl4h",
	"isOutFile":407,
	"isSch":621,
	"sch":{
		"schType":"19v44h",
		"schDate":"2018-10-30",
		"schTime":"2018-10-30 16:22:53",
		"isDataSource":588,
		"schCycleNum":"nx72bl",
		"dataSource":[
			""lyz8t4""
		]
	},
	"sqlInfo":[
		{
			"sql":"ozc10t",
			"fileType":"xncidf",
			"sqlName":"航.潘",
			"filePath":"iewg4x"
		}
	],
	"fileName":"航.潘"
}
```
**Response-fields:**

Field | Type|Description
---|---|---
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据
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
	"code":787,
	"msg":"htvyce",
	"data":[
		{
			"sceneId":"3b3gly",
			"jobId":617,
			"jobDesc":"mhl4qo",
			"jobType":"pnhtyd",
			"job":"51nlqo",
			"cond":"86k4fj",
			"parameter":"xwtyrq",
			"info":"qslyni",
			"retry":317,
			"timeout":169,
			"taskId":"87c91e",
			"status":"ctv7f8"
		}
	]
}
```

## 获取任务列表 //TODO 待测试
**URL:** null/m1/job/list

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
centerId|string|注册中心id|true
containerId|string|容器id|true
startDate|string|任务开始时间(yyyy-MM-dd)|false
endDate|string|任务结束时间(yyyy-MM-dd)|false
status|string|状态|false
cycle|string|周期(number/day/week/month)|false
name|string|名称(模糊搜索)|false
pageNo|int|页码|true
pageSize|int|页数|true


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
└─pageNo|int|当前页
└─pageSize|int|每页的数量
└─total|number|总记录数
└─data|array|结果集
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
	"code":540,
	"msg":"v52xr8",
	"data":{
		"pageNo":210,
		"pageSize":397,
		"total":321,
		"data":[
			{
				"jobId":"r6v31e",
				"jobName":"航.潘",
				"jobStatus":"mz4u2p",
				"schCycleNum":"8d7kvl",
				"condition":"whe6vp",
				"jobStartDateTime":"2018-10-30",
				"jobEndDateTime":"2018-10-30",
				"schType":"67hhmh"
			}
		]
	}
}
```

## 下载结果 //TODO 待实现
**URL:** null/m1/job/downloadResult

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
taskId|int|taskId|true


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


**Response-example:**
```
{
	"succ":true,
	"code":862,
	"msg":"xeknh9",
	"data":336
}
```

## 配置调度 //TODO 待测试
**URL:** null/m1/job/update/{jobId}

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
jobId|string|任务id|false
name|string|名称|true
execType|int|执行类型 0:保存调度 1:启用调度 2:执行任务调度(立即执行)|true
execFilePath|string|执行文件路径(绝对路径)|false
centerId|string|注册中心id|true
containerId|string|容器id|true
isOutFile|int|是否输出文件 (1:是 0:否)|true
isSch|int|是否配置调度(1:是 0:否)|true
sch|object|调度信息|false
└─schType|string|调度类型(number:次,day:日,week:周,month:月)|false
└─schDate|string|调度日期(yyyy-MM-dd)|false
└─schTime|string|调度时间(范围值 3-23)|false
└─isDataSource|int|是否配置数据源(1:有;0:否,isDataSource=1需配置dataSource,反之不需要配置)|true
└─schCycleNum|string|周期时间(例:周2-周日执行,范围 2-7)|false
└─dataSource|array|数据源信息|false
sqlInfo|array|sql信息|false
└─sql|string|sql内容|false
└─fileType|string|文件类型(如果isOutFile=0 则fileType可以传null)|false
└─sqlName|string|sql名称|false
└─filePath|string|sql文件路径|false
fileName|string|输出文件名称(如果isOutFile=0 则fileName可以传null)|false


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
	"code":148,
	"msg":"fvp0fp",
	"data":[
		{
			"sceneId":"9q577t",
			"jobId":837,
			"jobDesc":"glrf1h",
			"jobType":"6kse26",
			"job":"3umhee",
			"cond":"n96k18",
			"parameter":"tz7lfu",
			"info":"mixaxb",
			"retry":803,
			"timeout":916,
			"taskId":"wwud8k",
			"status":"fjrzw5"
		}
	]
}
```

## 查看日志 //TODO 待实现
**URL:** null/m1/job/log

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
taskId|int|taskId|true


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


**Response-example:**
```
{
	"succ":true,
	"code":951,
	"msg":"vgfaoe",
	"data":"giq6lo"
}
```

