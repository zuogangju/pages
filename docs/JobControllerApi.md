
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
	"msg":"h0n3qw",
	"data":[
		{
			"id":"rvp3x9",
			"title":"crvfzq"
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
	"msg":"c04i6k",
	"data":[
		{
			"tableName":"振家.冯",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"b3pp40"
		}
	]
}
```

## 获取数据源 //TODO 待测试
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
	"msg":"hhqtqm",
	"data":[
		{
			"id":"yr3wpf",
			"title":"0pvuh0"
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
	"msg":"56kwyl",
	"data":"ugem3z"
}
```

## 停止调度 //TODO 待实现
**URL:** http://{server}/m1/job/stop

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
	"name":"振家.冯",
	"taskId":"469uyh",
	"centerId":"8rr349",
	"containerId":"d2uasc",
	"sql":"888bpn",
	"fileType":"f5tybb",
	"sqlName":"振家.冯"
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
	"msg":"fazedg",
	"data":462
}
```

## 保存(保存调度信息)/启用调度信息(周期调度)/执行调度(立即执行) //TODO 待测试
**URL:** http://{server}/m1/job/save

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
	"jobId":"886k1m",
	"name":"振家.冯",
	"execType":978,
	"execFilePath":"wictnn",
	"centerId":"xpb523",
	"containerId":"urr85a",
	"isOutFile":330,
	"isSch":353,
	"sch":{
		"schType":"a5pg53",
		"schDate":"2018-10-26",
		"schTime":"2018-10-26 10:11:52",
		"isDataSource":101,
		"schCycleNum":"g30pqa",
		"dataSource":[
			""6ew8n5""
		]
	},
	"sqlInfo":[
		{
			"sql":"qlpbw8",
			"fileType":"robkcb",
			"sqlName":"振家.冯",
			"filePath":"p538uv"
		}
	],
	"fileName":"振家.冯"
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
	"msg":"g8jxpk",
	"data":[
		{
			"sceneId":"7jdb6m",
			"jobId":358,
			"jobDesc":"mectxs",
			"jobType":"50gfwr",
			"job":"rgw7k6",
			"cond":"gwrupj",
			"parameter":"5vb5fj",
			"info":"xcpebj",
			"retry":925,
			"timeout":499,
			"taskId":"oyq71w",
			"status":"kcmdrn"
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
centerId|string|注册中心id|true
containerId|string|容器id|true
startDate|string|任务开始时间(yyyy-MM-dd)|false
endDate|string|任务结束时间(yyyy-MM-dd)|false
status|string|状态|false
cycle|string|周期(number/day/week/month)|false
name|string|名称(模糊搜索)|false
pageNo|int|页码|false
pageSize|int|页数|false


**Request-example:**
```

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
	"msg":"egd2dz",
	"data":{
		"pageNo":297,
		"pageSize":363,
		"total":848,
		"data":[
			{
				"jobId":"1aoze2",
				"jobName":"振家.冯",
				"jobStatus":"afd1y6",
				"schCycleNum":"ywpw8z",
				"condition":"67mz2f",
				"jobStartDateTime":"2018-10-26",
				"jobEndDateTime":"2018-10-26",
				"schType":"2u924l"
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
	"msg":"6x514i",
	"data":270
}
```

## 配置调度 //TODO 待测试
**URL:** http://{server}/m1/job/update/{jobId}

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
	"msg":"t9m8sr",
	"data":[
		{
			"sceneId":"bcsfvp",
			"jobId":417,
			"jobDesc":"p5mave",
			"jobType":"4sqnw4",
			"job":"m2lkvr",
			"cond":"6xkato",
			"parameter":"9ejou4",
			"info":"4p9y0t",
			"retry":216,
			"timeout":357,
			"taskId":"s9dprp",
			"status":"xbx2p9"
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
	"msg":"xogdng",
	"data":"nc02hu"
}
```

