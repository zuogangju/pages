



# schweb接口文档

!> 文件类型 del,csv <br>
任务状态 WS:等待运行,SR:准备运行,RN:运行中,ES:运行完成,EF:运行失败,AC:等待执行引擎<br>
任务周期 number:次,day:日,week:周,month:月<br>
时间格式统一以yyyy-MM-dd/yyyy-MM-dd hh:mm:ss传输

## 获取用户信息
> **GET /m1/userinfo**

**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":{
				"instId": null,
				"userId": null,
				"userName": null,
				"agentInstId": null,
				"empnum": null,
				"emailbox": null,
				"ctttel": null,
				"status": null,
				"description": null,
				"registCenter":[
                                    {"id":"111","title":"银联科技事业部-注册中心1"},
                                    {"id":"222","title":"银联科技事业部-注册中心2"}
                               ]
			}
}
```
## 根据注册中心获取容器列表
> **GET /m1/regist/center/container?registId=111**

**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":[
				{"id":"111","title":"容器1"},
				{"id":"222","title":"容器2"}
           ]
}
```

## 元数据列表查询(支持模糊查询)
> **GET /m1/metadata/list?tableName=db.tableName&pageNo=1&pageSize=10**

**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":[
                {
                    "tableName":"db.tableName",
                    "fields":{"id": "string","name":"string","type":"string"}
                },
                {
                    "tableName":"db.tableName2",
                    "fields":{"id": "string","name":"string","type":"string"}
                }
          ]
}
```
## 获取数据源
> **GET /m1/datasource/list?**

**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":[
            {"id":"111","title":"数据源1"},
            {"id":"222","title":"数据源2"}
           ]
}
```
## 重新运行
> **POST /m1/job/start?jobId=111**

---
**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "启动成功",
	"data":"111"
}
```
## 停止任务调度
> **POST /m1/job/stop**

```json
{
	"jobId":"111",//任务id
	"centerId":"111",//注册中心id
	"containerId":"111"//容器id
}

```
---
**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":null
}
```

## 保存任务调度/启用任务调度信息/执行sql任务调度
> **POST /m1/job/save**

**请求参数**
> 次
```json
{
    "name":"POS",
    "execType":0,//0:保存调度 1:启用调度 2:执行任务调度(立即执行)
    "centerId":"111",//注册中心id
    "containerId":"111",//容器id
    "isOutFile":1,//是否输出文件  1:是 0:否
    "sqlInfo":[{
                "sql":"select * from table1",//sql语句
                "fileType?":"csv",//如果isOutFile=0 则fileType可以传null
                "sqlName?":"sql名称" //如果isOutFile=0 则fileName可以传null
              }],
    "fileName?":"压缩文件名称",//如果isOutFile=0 则fileName可以传null
    "isSch":1,//是否配置调度 1:是 0:否
    "sch?":{
                "schType":"number",//number:次,day:日,week:周,month:月
                "schDate":"2018-08-08",
                "schTime":"9-23", //9-23点执行   范围 0-23
                "isDataSource":0 //是否有数据源 1:有 ,0:否,isDataSource=1可不传时间相关的字段(schDate,schTime)
          }
}
```
> 日
```json
{
    "name":"POS",
    "execType":0,//0:保存调度 1:启用调度 2:执行任务调度(立即执行)
    "centerId":"111",//注册中心id
    "containerId":"111",//容器id
    "isOutFile":1,//是否输出文件  1:是 0:否
    "sqlInfo":[{
                "sql":"select * from table1",//sql语句
                "fileType?":"csv",//如果isOutFile=0 则fileType可以传null
                "sqlName?":"sql名称" //如果isOutFile=0 则fileName可以传null
              }],
    "fileName?":"压缩文件名称",//如果isOutFile=0 则fileName可以传null
    "isSch":1,//是否配置调度 1:是 0:否
    "sch?":{
                "schType":"day",// number:次,day:日,week:周,month:月
                "schDate":"2018-08-08",
                "schTime":"9-23", //9-23点执行   范围 0-23
                "isDataSource":1,//是否有数据源 1:有 ,0:否,isDataSource=1可不传时间相关的字段(schDate,schTime)
                "dataSource":["1111","2222"]//数据源id
            }
}
```
> 周
```json
{
    "name":"POS",
    "execType":0,//0:保存调度 1:启用调度 2:执行任务调度(立即执行)
    "centerId":"111",//注册中心id
    "containerId":"111",//容器id
    "isOutFile":1,//是否输出文件  1:是 0:否
    "sqlInfo":[{
                "sql":"select * from table1",//sql语句
                "fileType?":"csv",//如果isOutFile=0 则fileType可以传null
                "sqlName?":"sql名称"//如果isOutFile=0 则fileName可以传null
               }],
    "fileName?":"压缩文件名称",//如果isOutFile=0 则fileName可以传null
    "isSch":1,//是否配置调度 1:是 0:否
    "sch?":{
                "schType":"week",//number:次,day:日,week:周,month:月
                "schDate":"2018-08-08",
                "schTime":"9-23", //9-23点执行   范围 0-23
                "schCycleNum":"2-7",//  周2-周日执行  范围 1-7
                "isDataSource":1,//是否有数据源 1:有 ,0:否,isDataSource=1可不传时间相关的字段(schDate,schTime,schCycleNum)
                "dataSource":["1111","2222"]//数据源id
           }
}
```
> 月
```json
{
    "name":"POS",
    "execType":0,//0:保存调度 1:启用调度 2:执行任务调度(立即执行)
    "centerId":"111",//注册中心id
    "containerId":"111",//容器id
    "isOutFile":1,//是否输出文件  1:是 0:否
    "sqlInfo":[{
                "sql":"select * from table1",//sql语句
                "fileType?":"csv",//如果isOutFile=0 则fileType可以传null
                "sqlName?":"sql名称" //如果isOutFile=0 则fileName可以传null
              }],
    "fileName?":"压缩文件名称",//如果isOutFile=0 则fileName可以传null
    "isSch":1,//是否配置调度 1:是 0:否
    "sch?":{
                "schType":"week",//number:次,day:日,week:周,month:月
                "schDate":"2018-08-08",
                "schTime":"9-23", //9-23点执行   范围 0-23
                "schCycleNum":"2-15", // 2-15日执行   可选范围 1-31  
                "isDataSource":1,//是否有数据源 1:有 ,0:否,isDataSource=1可不传时间相关的字段(schDate,schTime,schCycleNum)
                "dataSource":["1111","2222"]//数据源id
            }
}
```
---
**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":null
}
```





## 获取任务列表
> **GET /m1/job/list**

**查询条件**
```json
{
    "centerId?":"111",//注册中心id
    "containerId?":"111",//容器id
    "startDateTime?":"2018-09-28",//开始时间
    "endDateTime?":"2018-10-28",//结束时间
    "status?":"成功",//任务状态
    "cycle?":"日",//任务周期
    "name?":"POS",//模糊搜索
    "pageNo":1,
    "pageSize":10
}


```
---
**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":{
		"pageNo":1,
		"pageSize":10,
		"total":1,
		"data":[{
                    "jobId": 1,
                    "jobName": "demoData",
                    "jobStatus": "demoData",
                    "schCycleNum": "demoData",
                    "condition": "demoData",
                    "jobStartDateTime": "1540191060062",
                    "jobEndDateTime": "1540191060062"
                }]
	}
}
```


## 下载结果
> **GET /m1/job/download?taskId=111**

**返回结果**
```text
正常下载文件

```


## 配置调度
> **POST /m1/job/update/{taskId}**
**请求参数**
```json
{
    "name":"POS",
    "execType":0,//0:保存 1:启用
    "centerId":"111",//注册中心id
    "containerId":"111",//容器id
    "isOutFile":1,//是否输出文件  1:是 0:否
    "sqlInfo":{
                "sql":["select * from table1","select * from table2"],//sql语句
                "fileType?":"csv",//如果isOutFile=0 则fileType可以传null
                "sqlName?":"文件名称" //如果isOutFile=0 则fileName可以传null
              },
    "isSch":1,//是否配置调度 1:是 0:否
    "sch":{
            "scheType":"0",//0:次,1:日,2:周,3:月
            "schDate":"2018-08-08",
            "schTime":"2-23",
            "schCycleNum":"2-15", // 2-15日执行   可选范围 1-31  
            "isDataSource":1, //是否有数据源 1:有 ,0:否,isDataSource=1可不传时间相关的字段(schDate,schTime,schCycleNum)
            "dataSource":["1111","2222"]//数据源id
          }
}
```
---
**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
	"data":null
}
```

## 查看日志
> **GET /m1/job/log?taskId=111**

**返回结果**
```json
{
    "succ": true,
    "code": 0,
    "msg": "操作成功",
    "data":"打印的日志信息"
}
```


