
# Description: 任务接口
## 刷新元数据
**URL:** http://{server}/m1/metadata/clear

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


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"ma6j9z",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 元数据列表查询(支持模糊查询) //TODO 待测试
**URL:** http://{server}/m1/metadata/list

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
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据
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
	"code":0,
	"msg":"6vgv7l",
	"data":[
		{
			"dbName":"子轩.陆",
			"tableName":"子轩.陆",
			"tableDesc":"2jmkrh",
			"fields":{
				"mapKey":{
					
				}
			},
			"filePath":"vpvrpw"
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
	"msg":"0stdqg",
	"data":[
		{
			"id":"j1bbnc",
			"title":"uaszsm"
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
	"msg":"fid6j8",
	"data":"1vwsx5"
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
	"name":"子轩.陆",
	"taskId":"2whhgt",
	"centerId":"0uax18",
	"containerId":"p98nyr",
	"sql":"3m6xfg",
	"fileType":"194dxk",
	"sqlName":"子轩.陆"
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
	"msg":"gt2mzy",
	"data":22
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
	"jobId":"jp810w",
	"jobNm":"2yt295",
	"jobDesc":"808pop",
	"execType":805,
	"execFilePath":"pnqtii",
	"centerId":"edoy1q",
	"containerId":"l0pmzy",
	"isOutFile":728,
	"isSch":727,
	"sch":{
		"schType":"c6p7o8",
		"schDate":"2018-12-27",
		"schTime":"2018-12-27 12:13:12",
		"isDataSource":894,
		"schCycleNum":"32405u",
		"dataSource":[
			""qv73qe""
		]
	},
	"sqlInfo":[
		{
			"sql":"gpsbtn",
			"fileType":"w1sk0t",
			"sqlName":"子轩.陆",
			"filePath":"002br7"
		}
	],
	"fileName":"子轩.陆"
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
	"msg":"h60h1p",
	"data":[
		{
			"sceneId":"wt35wo",
			"jobId":601,
			"jobDesc":"79k5jw",
			"jobType":"6zrilp",
			"job":"xvfqew",
			"cond":"jbcn0m",
			"parameter":"6id16j",
			"info":"cb4m2s",
			"retry":153,
			"timeout":405,
			"taskId":"6otgm5",
			"status":"83f2k1"
		}
	]
}
```

## 获取任务列表111 //TODO 待测试
**URL:** http://{server}/m1/job/list

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
pageNo|int|开始位置|true
pageSize|int|页数|true
search|string|模糊搜索内容|false
startDate|string|开始时间(yyyy-MM-dd)|false
endDate|string|结束时间(yyyy-MM-dd)|false
jobStatus|string|状态|false
cycle|string|周期(次:number/天:day/周:week/月:month)|false
centerId|string|注册中心id TODO MM|false
containerId|string|容器id  TODO MM|false


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
	"code":0,
	"msg":"rcf22l",
	"data":{
		"pageNo":239,
		"pageSize":455,
		"total":400,
		"data":[
			{
				"jobId":"oidpwa",
				"jobNm":"uid0h7",
				"jobDesc":"kuahss",
				"jobStatus":"gxl7cg",
				"jobExecPath":"iisqs1",
				"pjId":"rhlzhd",
				"jobParameter":"r2lgkp",
				"jobInfo":"r446c0",
				"userId":"nltd5u",
				"instId":"8hozjq",
				"jobStartDateTime":"2018-12-27",
				"jobEndDateTime":"2018-12-27"
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
	"msg":"kivdn3",
	"data":506
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
	"msg":"mc56xa",
	"data":[
		{
			"sceneId":"rkvppv",
			"jobId":905,
			"jobDesc":"lpnu05",
			"jobType":"5e6ffg",
			"job":"1h8byy",
			"cond":"iiqans",
			"parameter":"mq16i8",
			"info":"hpqi9i",
			"retry":857,
			"timeout":211,
			"taskId":"7kh5hi",
			"status":"ikwmuq"
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
	"msg":"yybgn1",
	"data":"k5hq9p"
}
```

## 创建JOB
**URL:** http://{server}/createJobs

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
businessDate|string|No comments found.|true
arrangedJobs|array|No comments found.|true
plainJobs|array|No comments found.|true


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
	"msg":"f22okc",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 启动任务
**URL:** http://{server}/reRunSchedule

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
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"astmwz",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 停止任务
**URL:** http://{server}/resetSchedule

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
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"12cp2z",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 查询日志
**URL:** http://{server}/resetSchedule

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
succ|boolean|成功返回true,失败返回false
code|int|响应代码
msg|string|接口响应信息
data|object|接口响应数据


**Response-example:**
```
{
	"succ":true,
	"code":0,
	"msg":"ck0ih6",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

