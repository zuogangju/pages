
# Description: 任务接口
## 根据注册中心获取容器列表 //TODO 待实现
**URL:** http://{server}/m1/regist/center/container

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
registId|string|注册中心id|true


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
└─id|string|id
└─title|string|容器


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"uoy218",
	"data":[
		{
			"id":"kgdgvu",
			"title":"4jzcba"
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
	"msg":"8q09f5",
	"data":[
		{
			"tableName":"峻熙.魏",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"l5yps7"
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
	"msg":"99rz0x",
	"data":[
		{
			"id":"xpdno5",
			"title":"e9q907"
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
	"msg":"gprn56",
	"data":"ht7pv8"
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
	"name":"峻熙.魏",
	"taskId":"oscrgb",
	"centerId":"x1s5uu",
	"containerId":"jsxilr",
	"sql":"pbcvvm",
	"fileType":"79a330",
	"sqlName":"峻熙.魏"
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
	"msg":"y8ert5",
	"data":280
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
	"jobId":"zidegb",
	"name":"峻熙.魏",
	"execType":2,
	"execFilePath":"op6d7h",
	"centerId":"gzqfdh",
	"containerId":"uy93kb",
	"isOutFile":158,
	"isSch":493,
	"sch":{
		"schType":"md6xvw",
		"schDate":"2018-12-21",
		"schTime":"2018-12-21 12:47:55",
		"isDataSource":36,
		"schCycleNum":"3vu0ht",
		"dataSource":[
			""n6xeb8""
		]
	},
	"sqlInfo":[
		{
			"sql":"kfaoa2",
			"fileType":"v93yed",
			"sqlName":"峻熙.魏",
			"filePath":"a7t232"
		}
	],
	"fileName":"峻熙.魏"
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
	"msg":"ay5fbx",
	"data":[
		{
			"sceneId":"6in00v",
			"jobId":507,
			"jobDesc":"t8pnte",
			"jobType":"udkxh8",
			"job":"ghb2l3",
			"cond":"3c1opg",
			"parameter":"fvtohd",
			"info":"5fva3r",
			"retry":270,
			"timeout":668,
			"taskId":"c5dtqm",
			"status":"p1syvu"
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
pageNo|int|页码|true
pageSize|int|页数|true


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
	"msg":"f7c16o",
	"data":{
		"pageNo":362,
		"pageSize":380,
		"total":370,
		"data":[
			{
				"jobId":"s0f3yy",
				"jobName":"峻熙.魏",
				"jobStatus":"3pi04u",
				"schCycleNum":"qo6o41",
				"condition":"4v50kd",
				"jobStartDateTime":"2018-12-21",
				"jobEndDateTime":"2018-12-21",
				"schType":"ryqm2p"
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
	"msg":"5yh7oo",
	"data":571
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
No Request-example
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
	"msg":"q1jgi1",
	"data":[
		{
			"sceneId":"1wd0rp",
			"jobId":686,
			"jobDesc":"efxgb9",
			"jobType":"3gc1gj",
			"job":"w77mqx",
			"cond":"wnomsh",
			"parameter":"5cvfor",
			"info":"6pxisf",
			"retry":784,
			"timeout":229,
			"taskId":"wh3b2w",
			"status":"m0bu2e"
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
	"msg":"r9z1fu",
	"data":"wxrch9"
}
```

