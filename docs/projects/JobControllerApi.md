
# Description: 任务接口
## 刷新元数据
**URL:** null/m1/metadata/clear

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


**Response-example:**
```
{
	"succ":true,
	"code":937,
	"msg":"9einbi",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 元数据列表查询(支持模糊查询) //TODO 待测试
**URL:** null/m1/metadata/list

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
search|string|  表名称(支持模糊查询)|false
pageNo|int|  页码|true
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
└─dbName|string|No comments found.
└─tableName|string|表名称
└─tableDesc|string|表描述
└─fields|map|字段信息{"id":"string","name":"string","type":"string"}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─any object|object|any object.
└─filePath|string|存储路径信息


**Response-example:**
```
{
	"succ":true,
	"code":582,
	"msg":"02e064",
	"data":[
		{
			"dbName":"博文.吕",
			"tableName":"博文.吕",
			"tableDesc":"zsohlm",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"lu54z4"
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
	"code":969,
	"msg":"nht5vn",
	"data":[
		{
			"id":"1dicn7",
			"title":"yx7ql1"
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
	"code":683,
	"msg":"gob8ms",
	"data":"ox7dum"
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
	"name":"博文.吕",
	"taskId":"9o4fap",
	"centerId":"t4pev5",
	"containerId":"9w3vzc",
	"sql":"7tr9df",
	"fileType":"i4wbzk",
	"sqlName":"博文.吕"
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
	"code":427,
	"msg":"iwibpk",
	"data":440
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
jobNm|string|名称|true
jobDesc|string|任务描述|true
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
	"jobId":"0ha0w8",
	"jobNm":"l517z1",
	"jobDesc":"4r9qmk",
	"execType":491,
	"execFilePath":"w3kjl5",
	"centerId":"na3fwi",
	"containerId":"d5e7v3",
	"isOutFile":395,
	"isSch":496,
	"sch":{
		"schType":"3oksgo",
		"schDate":"2018-12-26",
		"schTime":"2018-12-26 16:01:08",
		"isDataSource":273,
		"schCycleNum":"d4zte7",
		"dataSource":[
			""39ewmn""
		]
	},
	"sqlInfo":[
		{
			"sql":"n94btz",
			"fileType":"b5prcr",
			"sqlName":"博文.吕",
			"filePath":"k3jkbq"
		}
	],
	"fileName":"博文.吕"
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
	"code":745,
	"msg":"erf0gq",
	"data":[
		{
			"sceneId":"5aigkn",
			"jobId":487,
			"jobDesc":"l36qkk",
			"jobType":"vvh47z",
			"job":"f480w5",
			"cond":"lzrjc3",
			"parameter":"haq526",
			"info":"1c261a",
			"retry":373,
			"timeout":229,
			"taskId":"g04es0",
			"status":"wgbo77"
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
startDate|string|任务开始时间(yyyy-MM-dd)|false
endDate|string|任务结束时间(yyyy-MM-dd)|false
jobStatus|string|状态|false
cycle|string|周期(次:number/天:day/周:week/月:month)|false
search|string|名称(模糊搜索)|false
pageNo|int|页码|true
pageSize|int|页数|true
userId|string|用户id|false
centerId|string|注册中心id TODO MM|false
containerId|string|容器id  TODO MM|false


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
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobNm|string|任务名称
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobDesc|string|任务描述
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobStatus|string|任务状态
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobExecPath|string|脚本路径
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─pjId|string|项目id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobParameter|string|任务参数
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobInfo|string|job请求参数信息(用于前台回显)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─userId|string|用户id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─instId|string|机构id
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobStartDateTime|string|任务开始时间
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└─jobEndDateTime|string|任务结束时间


**Response-example:**
```
{
	"succ":true,
	"code":953,
	"msg":"mqv0fb",
	"data":{
		"pageNo":377,
		"pageSize":127,
		"total":355,
		"data":[
			{
				"jobId":"btjq30",
				"jobNm":"iq21b9",
				"jobDesc":"h6zuu4",
				"jobStatus":"porjjo",
				"jobExecPath":"vs30b6",
				"pjId":"pjrma5",
				"jobParameter":"06bumy",
				"jobInfo":"08nnwi",
				"userId":"hntweh",
				"instId":"e4m92i",
				"jobStartDateTime":"2018-12-26",
				"jobEndDateTime":"2018-12-26"
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
	"code":117,
	"msg":"9d1e5h",
	"data":889
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
jobNm|string|名称|true
jobDesc|string|任务描述|true
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
	"code":355,
	"msg":"ppvlhm",
	"data":[
		{
			"sceneId":"6hkrvq",
			"jobId":8,
			"jobDesc":"komhtf",
			"jobType":"scw19v",
			"job":"se96d2",
			"cond":"9o1xy3",
			"parameter":"dawjle",
			"info":"0t6zc0",
			"retry":916,
			"timeout":914,
			"taskId":"oqa968",
			"status":"sjnwhj"
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
	"code":207,
	"msg":"7te28u",
	"data":"e40ga3"
}
```

## 创建任务并启动
**URL:** null/createJobs

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
businessDate|string|No comments found.|true
type|int|No comments found.|true


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
	"code":202,
	"msg":"e7zgqr",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 启动任务
**URL:** null/reRunSchedule

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
businessDay|string|No comments found.|true
sceneId|string|No comments found.|true
skdId|int|No comments found.|true


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
	"code":684,
	"msg":"uftx0g",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 停止任务
**URL:** null/resetSchedule

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
businessDay|string|No comments found.|true
code|int|No comments found.|true
remark|string|No comments found.|true
skdid|int|No comments found.|true
status|string|No comments found.|true


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
	"code":585,
	"msg":"onyi52",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 查询日志
**URL:** null/resetSchedule

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|No comments found.|true
path|string|No comments found.|true
start|int|No comments found.|true
limit|int|No comments found.|true


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
	"code":428,
	"msg":"p7z9pc",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

