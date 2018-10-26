
# Description: 任务接口
## 根据注册中心获取容器列表 //TODO 待实现
**URL:** null/m1/regist/center/container

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
registId|string|注册中心id|false


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
└─id|string|id
└─title|string|容器


**Response-example:**
```
{
	"succ":true,
	"code":765,
	"msg":"ak11h7",
	"data":[
		{
			"id":"ztk7dm",
			"title":"usbh15"
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
tableName|string|表名称(支持模糊查询)|true
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
	"code":538,
	"msg":"f3hcmy",
	"data":[
		{
			"tableName":"钰轩.洪",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"5ojfyi"
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
	"code":744,
	"msg":"42i24u",
	"data":[
		{
			"id":"cfwurh",
			"title":"vc3bq3"
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
	"code":127,
	"msg":"tq8ttb",
	"data":"osvny3"
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
	"name":"钰轩.洪",
	"taskId":"g1hf6k",
	"centerId":"lw2fya",
	"containerId":"gnhn23",
	"sql":"7vkg1p",
	"fileType":"gnebyw",
	"sqlName":"钰轩.洪"
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
	"code":811,
	"msg":"9dgvft",
	"data":636
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
	"jobId":"px8ffh",
	"name":"钰轩.洪",
	"execType":937,
	"execFilePath":"xjx6el",
	"centerId":"6g7d8m",
	"containerId":"sngnto",
	"isOutFile":66,
	"isSch":771,
	"sch":{
		"schType":"ohqv9l",
		"schDate":"2018-10-26",
		"schTime":"2018-10-26 10:33:07",
		"isDataSource":367,
		"schCycleNum":"qb1hfe",
		"dataSource":[
			""nan6d3""
		]
	},
	"sqlInfo":[
		{
			"sql":"qc7k5z",
			"fileType":"nnv720",
			"sqlName":"钰轩.洪",
			"filePath":"sush1j"
		}
	],
	"fileName":"钰轩.洪"
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
	"code":132,
	"msg":"q0nssj",
	"data":[
		{
			"sceneId":"at5c0n",
			"jobId":463,
			"jobDesc":"o280fp",
			"jobType":"uwd601",
			"job":"dze0ip",
			"cond":"w5mzc9",
			"parameter":"k4sw6q",
			"info":"a8t3zg",
			"retry":224,
			"timeout":751,
			"taskId":"cohx2y",
			"status":"9g4t6m"
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
└─pageNo|int|No comments found.
└─pageSize|int|No comments found.
└─total|number|No comments found.
└─data|array|No comments found.
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
	"code":212,
	"msg":"6voddo",
	"data":{
		"pageNo":483,
		"pageSize":607,
		"total":820,
		"data":[
			{
				"jobId":"5achis",
				"jobName":"钰轩.洪",
				"jobStatus":"d77353",
				"schCycleNum":"blbpcj",
				"condition":"nmpw0x",
				"jobStartDateTime":"2018-10-26",
				"jobEndDateTime":"2018-10-26",
				"schType":"g4r759"
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
	"code":305,
	"msg":"y96gkd",
	"data":451
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
	"code":615,
	"msg":"2p71oj",
	"data":[
		{
			"sceneId":"tj9del",
			"jobId":545,
			"jobDesc":"ckva91",
			"jobType":"qc6grm",
			"job":"akifkl",
			"cond":"86lt57",
			"parameter":"azzx20",
			"info":"4j6qzx",
			"retry":368,
			"timeout":968,
			"taskId":"eeo5wc",
			"status":"zzmky9"
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
	"code":671,
	"msg":"tkezg7",
	"data":"w7qx93"
}
```

