# 数据库管理接口的定义

**数据库的数据格式定义  Database**

```json
{
  "dbName":"default",   //数据库名称
  "createUserId":"yjy1",
  "createUserName":"yjy1",
  "createInstId":"00010000",//创建用户机构ID
  "createInstName":"00010000",//创建用户机构Name
  "createTime":124545454545,
  "updateTime":124545454545,
  "ownInstId"? :"0800010000", // 所属机构的Id 私有库有效
  "ownInstName"?:"机构名称", // 所属机构的Name 私有库有效
  "isPublic":0/1   //是否公共数据库
}
```



## 1. 获取库

***GET请求:*** **/database/list**

**请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有 1 是公有 空 是所有
    "dbName": string // 模糊查询的数据库名称
}
```

**返回参数**

```JSON
PagiGation // 页码对象
data: [
    {
      "dbName":"default",   //数据库名称
      "createUserId":"yjy1",
      "createUserName":"yjy1",
      "createInstId":"00010000",//创建用户机构ID
      "createInstName":"00010000",//创建用户机构Name
      "createTime":124545454545,
      "updateTime":124545454545,
      "ownInstId"? :"0800010000", // 所属机构的Id 私有库有效
      "ownInstName"?:"机构名称", // 所属机构的Name 私有库有效
      "isPublic":0/1   //是否公共数据库
    }
]
```
## 2.创建数据库

***POST请求:*** **/database/create** 

**请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有库  1 是 公有库
    "dbName": string, // 数据库名称
    "dbDesc"?: string, // 数据库的描述，可以为空
    "ownInstId": string,  // 所属机构ID
}
```

**返回结果**

```json
{
	"succ": true | false, // true 创建成功 false 失败
  	...
}
```

## 3. 删除数据库

***POST请求*** **/database/delete**

**请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有库  1 是 公有库
    "dbName": string; // 数据库名称
    "ownInstId": string,  // 所属机构ID
}
```

**返回结果**

```json
Status // 状态对象
{
    succ: true;
}
```

## 4. 查看数据库下的表

***GET请求*** **/sourcetables**

(同表管理的接口一直)

**请求参数**

```json
{
    "pageSize": number,
    "pageNo": number,
    "dbName": string,
    "tableName": string
}
```

**返回结果**

```json
PagiGation // 分页对象
data: [
	{
      "createTime": 1505201617000,
      "tableTypeCd": "1111",
      "tableDesc": "tabledesc",
      "tableId": 1,
      "updateTime": 1505201617000,
      "tableName": "tablename",
      "tablePropCd": "tablepro",
      "tableAlias": "tablealias",
      "ddl": "ddl",
      "createInstId": "0800010000",
      "createUserId": "111"
	}
]
```

## 5. 查看建表语句

同表管理 

**(TableId 替换成  dbName + TableName 两个字段)**

## 6. 查看表字段

同表管理

## 7.  查看表的权限用户列表

***GET请求*** **/sourcetable/auth/view/{authlevel}**

**请求参数**

```json
{
    "pageNo": 1,
    "pageSize": 100, // 获取所有用户
    "dbName": string, // 数据库名称
    "tableName": string, // 表名称
}
```

**返回结果**

```json
PagiGation // 分页对象
data: [
    {
        UserInfo({
            "auth": 0 | 1 | 2; // 0 读  1 写 2 ALL
        }),      
    }
]
```

### 7.1  获取公共数据库下用户的字段权限

***GET请求*** **/sourcetable/auth/field**

**请求参数**

```json
{
        "dbName": string,
        "tableName": string,
  	"userId": string,
        "instId": string,
  	"uid": string
}
```

**返回参数**

```json
State
data: [
    {
        fieldName: string, // 字段名称
      	filedDesc: string, // 可没有
      	active: true // 是否有该字段的权限
    }
]
```

### 7.2 删除用户权限

***POST请求*** **/sourcetable/users/auth/delete**

**请求参数**

```json
{
    "dbName": string,
    "tableName": string,
    "users": [
        {
            "userId": string,
            "instId": string,
            "uid": string
        }
    ]
}
```

**返回参数**

```json
Status
{
    "succ": boolean;
}
```

### 7.3 删除用户权限字段  共有表

***POST请求*** **/sourcetable/fields/auth/delete**

**请求参数**

```json
{
    "userId": string,
    "instId": string,
    "fields": [
        {
           "fieldName": string;
        }, {
           "fieldName": string; // 前端过滤    
        }
    ]
}
```

**返回参数**

```json
Status
{
    "succ": boolean;
}
```



### 7.4 添加用户权限

#### 7.4.1 获取用户列表

***GET 请求*** **/sourcetable/users**

**请求参数**

```json
{
    "instId": string;
    "dbName": string;
    "tableName": string;
    "pageNo": number;
    "pageSize": number; // 100
}
```

**返回参数**

```
PagiGation
data: [
  {
    UserInfo对象({
      ...
      active: true | false
    })
  }
]
```

#### 7.4.2 添加用户 (私有)

***POST请求*** **/sourcetable/add/users**

**请求参数**

```json
{
    "dbName": string;
    "tableName": string;
    "users": [
    	{
    		"userId": string;
     		"instId": string;
  		"uid": string;
  		"auth": 0 | 1 | 2; // 0 读  1 写 2 ALL
		}
    ]
}
```

**返回结果**

```json
Status
{
    succ: true | false
}
```



### 7.5 修改表的用户权限

***POST请求*** **/sourcetable/users/auth/update**

**请求参数**

```json
{
    "dbName": string;
    "tableName": string;
    "users": [
    	{
    		"userId": string;
     		"instId": string;
  		"uid": string;
  		"auth": 0 | 1 | 2; // 0 读  1 写 2 ALL
		}
    ]
}
```

**返回结果**

```json
Status
{
    succ: true | false
}
```

### 7.6获取用户下的表数

***GET请求*** **/sourcetable/totaltable**

**返回参数**

```json
Status
{
    "succ": boolean;
    “data”:int;
}
```

# job和task日志相关
### 8.根据用户获取项目下的可执行文件

***GET请求*** **{projectId}/project/job/**

**返回参数**

```json
Status
{
    "succ": boolean;
    “data”:[
                    {"projectId":1,"jobId":1,"name":"111","exeEngine":"hivesql","execFileAddr":"hivesql"}
               ];
}
```
### 9.运行任务

***GET请求*** **{projectId}/sch/job/{jobId}/run**

**返回参数**

```json
Status
{
    "succ": true/false;
}
```
### 10.停止任务

***GET请求*** **{projectId}/sch/job/{taskId}/stop**

**返回参数**

```json
Status
{
    "succ": true/false;
}
```
### 10.查看job的所有运行实例

***GET请求*** **{projectId}/sch/job/tasks/{jobId}?pageNo=1&pageSize=10**

**返回参数**

```json
{
    "succ": true,
    "msg": "ok",
    "code": 0,
    "data": {
        "data": [
            {
                "taskId": 1567,
                "runWfId": 8313,
                "status": "SR",
                "crtTime": 1511750463000,
                "uptTime": 1511750463000
            }
        ],
        "pageSize": 10,
        "currentPage": 1,
        "totalCount": 53
    }
}
```

### 11.查看任务日志 下翻

***GET请求*** **{projectId}/sch/task/log/{type}/{taskId}/{currFileSize}**
type  0:上翻、1:下翻

**返回参数**

```json
{
    "succ": true,
    "msg": "ok",
    "code": 0,
    "data": {"lastFileSize":0,"logMsg":"错误日志信息"}
}
```