# 数据库管理接口的定义

## **数据库的数据格式定义  Database**

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

> **请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有 1 是公有 空 是所有
    "dbName": string // 模糊查询的数据库名称
}
```

> **返回参数**

```json
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

> **请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有库  1 是 公有库
    "dbName": string, // 数据库名称
    "dbDesc"?: string, // 数据库的描述，可以为空
    "ownInstId": string,  // 所属机构ID
}
```

> **返回结果**

```json
{
    "succ": true | false // true 创建成功 false 失败
}
```

## 3. 删除数据库

***POST请求*** **/database/delete**

> **请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有库  1 是 公有库
    "dbName": string; // 数据库名称
    "ownInstId": string,  // 所属机构ID
}
```

> **返回结果**

```json
Status // 状态对象
{
    succ: true;
}
```
## 4.更新数据库

***POST请求:*** **/database/update**

> **请求参数**

```json
{
    "isPublic": 0 | 1, // 0 是私有库  1 是 公有库
    "dbName": string, // 数据库名称
    "dbDesc"?: string, // 数据库的描述，可以为空
    "ownInstId": string,  // 所属机构ID
}
```

> **返回结果**

```json
{
    "succ": true | false // true 修改成功 false 失败
}
```

```json
{"tableId":0,"dbName":"str","tableName":"str","tableDesc":"str","tablePropCd":"str","tableTypeCd":"str","createUserId":"str","createInstId":"str","createTime":1525248773184,"updateTime":1525248773184,"status":"str","updateUserId":"str","updateInstId":"str","storageCycle":0,"ddl":"str"}
```