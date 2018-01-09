### 创建job
**POST  /{projectId}/sch/job/new**
**请求参数**
```json
{
    "name": "job名称",
    "exeEngine": "SHELL", 
    "execFileAddr": "a/b/c", 
    "desc": "ddd",
    "jobParam": "job参数"
}
```
**返回结果**
```json
{
    "succ": true,
    "msg": "删除成功",
    "code": 0,
    "data": true
}
```

### 删除job
**GET  /{projectId}/sch/job/delete/{jobId}**
**请求参数**
```json
{
    "projectId":"int",
    "jobId":"int"
}
```
**返回结果**
```json
{
    "succ": true,
    "msg": "删除成功",
    "code": 0,
    "data": true
}
```
### 查询job详情
**GET  /{projectId}/sch/job/detail/{jobId}**
**请求参数**
```json
{
    "projectId":"int",
    "jobId":"int"
}
```
**返回结果**
```json
{
    "succ": true,
    "msg": "删除成功",
    "code": 0,
    "data": {
     "userId":"yjy1",
     "instId":"00010000",
     "projectId":1545458451222,
     "jobId":33,
     "jobParam":"执行参数",
     "name":"job名称",
     "exeEngine":"HIVE",
     "execFileAddr":"/select.sh",
     "desc":"job描述"
    
    }
}
```
### 根据用户信息查询所有任务流实例

**GET  /sch/wf/wfRun/list**

**请求参数**
```json
{
    "pageNo": 1,
    "pageSize ":10,
    "wfName": "任务流",
    "wfDesc": "描述",
    "beginTime":"20170202",
    "endTime":"20170202"
}

```


**返回结果**

```json
{
    "succ": true,
    "code": 0,
    "msg": "ok",
    "data": {
        "currentPage": 1,
        "pageSize": 10,
        "totalCount": 1,
        "data": [
            {
                "projectId": "1213132121",//项目id
                "wfName": "test_sche",//任务流名称
                "wfDesc": "12345",//任务流描述
                "type": 1,//0:非调度任务；1：调度任务
                "runWfId": "4115",//实例id
                "status": "运行完成",//运行状态
                "beginTime": 1514967325000,//开始时间
                "endTime": 1514967325000   //结束时间
            }
        ]
    }
}
```