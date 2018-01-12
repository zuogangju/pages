# 资源管理接口

## 审计日志管理

### 根据指定条件查询审计日志

> **GET  /logs**

!> [模块名称](http://172.20.112.122:8080/mizar/log/moduleType)
 [操作类型](http://172.20.112.122:8080/mizar/log/optType)

> > **请求参数**

```json
{
    "userId": "yjy1",//用户id-模糊查询
    "instId": "0800010000",//机构id-模糊查询
    "description": "str",//描述-模糊查询
    "errorMsg": "str", //错误信息-模糊查询
    "moduleName": "api",//模块名称-下拉(/log/moduleType)
    "operType": "query",//操作类型-下拉(/log/optType)
    "operStatus": "S",//操作状态
    "operDatatimeStart": "2017-12-05",//开始时间
    "operDatatimeEnd": "2017-12-12",//结束时间
    "pageNo": 1,//页码
    "pageSize": 10 //每页显示条数
}
```

> > **返回结果**

```json
{
  "data": {
    "data": [
      {
        "description": "创建API授权协议信息,表名：tbl_bdp_fe_api_agree_info",
        "operDatatime": 1512447480000,
        "createDatatime": 1512447481000,
        "instId": "0800010000",
        "userId": "yjy1",
        "errorMsg": "",
        "moduleName": "api",
        "operType": "add",
        "operStatus": "S",
        "logId": 10
      }
    ],
    "totalCount": 10,
    "pageSize": 10,
    "currentPage": 1
  },
  "succ": true,
  "msg": null,
  "code": 0
}
```

### 根据类型查询下拉条件

> **GET  /log/{cdType}**

---

> **返回结果**

```json
{
  "data": [
    {
      "codeDesc": "关联",
      "code": "join"
    }
  ],
  "code": 0,
  "msg": null,
  "succ": true
}
```

## 参数管理相关接口

### 查询参数列表

> **GET  /dim**

---

> **请求参数**

```json
{
    "pageNo":1,
    "pageSize":10,
    "code":"str",
    "cdTp":"str",
    "codeDesc": "str",
    "createUserId": "str",
    "createInstId": "str",
    "createTime": 1513047419898,
    "updateTime": 1513047419898
}
```

> **返回结果**

```json
{
  "data": {
    "data": [
      {
        "createInstId": "800010000",
        "createUserId": "yjy1",
        "updateTime": 1505387220000,
        "createTime": 1505387220000,
        "codeDesc": "SM3(商户编号)",
        "cdTp": "apiFunctionType",
        "code": "1"
      }
    ],
    "currentPage": 1,
    "totalCount": 2,
    "pageSize": 10
  },
  "msg": null,
  "succ": true,
  "code": 0
}
```

### 查询参数类型

> **GET  /dim/cdTp/list**

---

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
  "data": [
    {
      "cdTp": "apiFunctionType"
    },
    {
      "cdTp": "apiType"
    },
    {
      "cdTp": "fieldAuth"
    },
    {
      "cdTp": "resourceType"
    },
    {
      "cdTp": "secretKey"
    },
    {
      "cdTp": "optType"
    },
    {
      "cdTp": "moduleType"
    }
  ],
  "msg": "操作成功",
  "succ": true,
  "code": 0
}
```

### 根据类型查询参数列表

> **GET  /dim/{cdTp}**

---

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
  "data": [
    {
      "createInstId": "800010000",
      "createUserId": "yjy1",
      "updateTime": 1505387220000,
      "createTime": 1505387220000,
      "codeDesc": "API",
      "cdTp": "moduleType",
      "code": "api"
    }
  ],
  "msg": "操作成功",
  "succ": true,
  "code": 0
}
```

### 根据类型添加参数

> **POST  /dim/{cdTp}/add**

---

> **请求参数**

```json
{
  "code": "project",
  "codeDesc": "项目模块"
}
```

> **返回结果**

```json
{
  "data": null,
  "msg": "操作成功",
  "succ": true,
  "code": 0
}
```

### 根据类型更新参数

> **POST  /dim/{cdTp}/{code}/update**

---

> **请求参数**

```json
{
  "codeDesc": "项目模块"
}
```

> **返回结果**

```json
{
  "data": null,
  "msg": "操作成功",
  "succ": true,
  "code": 0
}
```

### 根据类型删除参数

> **POST  /dim/{cdTp}/delete**

---

> **请求参数**

```json
{
  "code": "project"
}
```

> **返回结果**

```json
{
  "data": null,
  "msg": "操作成功",
  "succ": true,
  "code": 0
}
```

## 申请汇总接口

### 申请汇总列表（资源申请、api申请、公共数据申请）

> **GET  /apply/list?pageNo=1&pageSize=10**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)
</br> 申请类型 4:API申请；5：公共数据申请；其他:资源申请
</br> [申请类型](http://172.20.112.122:8080/mizar/dim/applyType) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **返回结果**

```json
{
  "data": {
    "data": [
       {
        "orderId": "api_0800010000_1512980759863",//单号
        "applyType": "2",//申请类型(/dim/applyType)
        "description": "订单描述",//订单描述
        "remark": "审核通过",//审核描述
        "applyReason": "申请原因",//申请描述
        "reviewStatus": "3",//审核状态(/dim/reviewStatus)
        "applyUserId": "yjy1",
        "applyInstId": "0800010000",
        "updateTime": 1513061139000,
        "createTime": 1513061138000
      }
    ],
    "pageSize": 10,
    "currentPage": 1,
    "totalCount": 1
  },
  "succ": true,
  "msg": null,
  "code": 0
}
```

## API申请相关接口

### 查询API申请

> **GET  /apiApply/list?pageNo=1&pageSize=10**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)
</br> [申请API名称](http://172.20.112.122:8080/mizar/dim/apiType) [申请类型](http://172.20.112.122:8080/mizar/dim/apiApplyType) [输出是否涉密](http://172.20.112.122:8080/mizar/dim/exportType) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus) [API功能](http://172.20.112.122:8080/mizar/dim/apiFunctionType)

> **返回结果**

```json
{
  "data": {
    "data": [
      {
        "apiOrderId": "api_0800010000_1512980759863",//申请单号*
        "applyType": "4",//申请类型（/dim/apiApplyType）
        "applyTypeName": "API调用",//申请类型*
        "description": "3",//单号描述*
        "applyReason": "临时使用",//申请原因*
        "applyInstId": "0800010000",//申请单位*
        "applyUserId": "yjy1",//申请用户*
        "reviewStatus": "3",//审核状态（/dim/reviewStatus）
        "reviewStatusName": "草稿",//审核状态*
        "remark": "3",//审核原因*
        "updateTime": 1511849445000,//创建时间*
        "createTime": 1511849445000,//更新时间*

        "apiType": "1",//申请API名称（/dim/apiType）
        "apiTypeName": "1",//申请API名称
        "exportType": "3",//输出是否涉密（/dim/exportType）
        "exportTypeName": "3",//输出是否涉密
        "concurrent": 2,//并发量
        "useFrequency": 3,//使用频率
        "appName": "应用名称",//应用名称
        "mchntId": "mchnt_0800010000_1512980759863",//商户id
        "mchntName": "商户名称",//商户名称
        "secretKey": "APPID_1513056202636_A2126CAE-5DAC-4955-8557-D19AF98CC940",//密钥
        //申请人信息
        "applyUserName": "yjy1",
        "applyInstName": "上海总公司",
        //审核人信息
        "reviewUserId": "yjy1",
        "reviewUserName": "yjy1",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海总公司",
        "otherRequire": "其它筛选条件",//其它筛选条件
        "apiFunctionType": "1",//API功能（/dim/apiFunctionType）
        "apiFunctionTypeName": "1",//API功能
        "exportFields": "3",//输出字段
        "applyApiId": "api_1_1512980759863",//申请APIID
        "appId": "application_0800010000_1512980759863"//应用id
      }
    ],
    "pageSize": 10,
    "currentPage": 1,
    "totalCount": 1
  },
  "succ": true,
  "msg": null,
  "code": 0
}
```

### 查询API申请详细信息

> **GET  /apiApply/{apiOrderId}/detail**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)</br>
 [申请API名称](http://172.20.112.122:8080/mizar/dim/apiType) [申请类型](http://172.20.112.122:8080/mizar/dim/apiApplyType) [输出是否涉密](http://172.20.112.122:8080/mizar/dim/exportType) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus) [API功能](http://172.20.112.122:8080/mizar/dim/apiFunctionType)

> **返回结果**

```json
{"data": {
        "apiOrderId": "api_0800010000_1512980759863",
        "applyType": "4",//申请类型（/dim/apiApplyType）
        "applyTypeName*": "API调用",//申请类型
        "description": "3",//单号描述
        "applyReason": "临时使用",//申请原因
        "applyInstId": "0800010000",//申请单位
        "applyUserId": "yjy1",//申请用户
        "reviewStatus": "3",//审核状态（/dim/reviewStatus）
        "reviewStatusName": "草稿",//审核状态
        "remark": "3",//审核原因
        "updateTime": 1511849445000,
        "createTime": 1511849445000,
        "apiType": "1",//申请API名称（/dim/apiType）
        "apiTypeName": "1",//申请API名称
        "exportType": "3",//输出是否涉密（/dim/exportType）
        "exportTypeName": "3",//输出是否涉密
        "concurrent": 2,//并发量
        "useFrequency": 3,//使用频率
        "appName": "应用名称",//应用名称
        "mchntId": "mchnt_0800010000_1512980759863",//商户id
        "mchntName": "商户名称",//商户名称
        "secretKey": "APPID_1513056202636_A2126CAE-5DAC-4955-8557-D19AF98CC940",//密钥
        //申请人信息
        "applyUserName": "yjy1",
        "applyInstName": "上海总公司",
        //审核人信息
        "reviewUserId": "yjy1",
        "reviewUserName": "yjy1",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海总公司",
        "otherRequire": "其它筛选条件",//其它筛选条件
        "apiFunctionType": "1",//API功能（/dim/apiFunctionType）
        "apiFunctionTypeName": "1",//API功能
        "exportFields": "3",//输出字段
        "applyApiId": "api_1_1512980759863",//申请APIID
        "appId": "application_0800010000_1512980759863"//应用id
      },
  "succ": true,
  "msg": null,
  "code": 0
}
```

### 创建API申请

> **POST  /apiApply/add**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)
</br> 注：如果输入内容涉及到卡或者商户相关信息，需要用户必须上传授权协议

* apiFunctionType:API功能
* 1、SM3(商户编号）
* 2、SM3(卡号，或token号) 注：卡号字段的前两位为卡号长度
* 3、卡号（或token号）前6+后4
* 4、商户编号（明文）
* 5、SM3商户编号
* 6、卡号（明文）列表
* 7、SM3卡号列表
* 8、商户号（明文）列表
* 9、SM3商户号列表
* 10、SM3(商户编号）+ 受理机构代码末4位（即:城市代码)
* [申请API名称](http://172.20.112.122:8080/mizar/dim/apiType) [申请类型](http://172.20.112.122:8080/mizar/dim/apiApplyType) [输出是否涉密](http://172.20.112.122:8080/mizar/dim/exportType) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus) [API功能](http://172.20.112.122:8080/mizar/dim/apiFunctionType)

> **请求参数**

```json
 {
    "apiFunctionType": "string", //下拉（/dim/apiFunctionType）
    "mchntId": "string",//商户id
    "mchntName": "string",//商户名称
    "apiType": "string",//申请API名称-下拉（/dim/apiType）
    "appName": "string",//应用名称
    "applyReason": "string",//申请理由
    "applyType": "string",//申请类型（4-API调用）（/dim/apiApplyType）
    "concurrent": 0, //并发量
    "description": "string",//描述
    "exportFields": "string",//输出字段(用户描述输出字段)
    "exportType": "string",//输出是否涉密（/dim/exportType）
    "otherRequire": "string",//其它筛选条件(用户描述筛选条件或选择筛选条件)
    "reviewStatus": "0",//审核状态（/dim/reviewStatus）
    //使用频率
    "useFrequency": 0
  }
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "创建成功",
    "code": 0,
    "data": true
}
```

### 删除API申请

> **POST  /apiApply/delete/{apiOrderId}**

---

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "删除成功",
    "code": 0,
    "data": true
}
```

### 更新API申请

> **POST  /apiApply/update/{apiOrderId}**
> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)
* [申请API名称](http://172.20.112.122:8080/mizar/dim/apiType) [申请类型](http://172.20.112.122:8080/mizar/dim/apiApplyType) [输出是否涉密](http://172.20.112.122:8080/mizar/dim/exportType) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus) [API功能](http://172.20.112.122:8080/mizar/dim/apiFunctionType)

> **请求参数**

```json
{
    "apiFunctionType": "string", //下拉（/dim/apiFunctionType）
    "mchntId": "string",//商户id
    "mchntName": "string",//商户名称
    "apiType": "string",//申请API名称-下拉（/dim/apiType）
    "appName": "string",//应用名称
    "applyReason": "string",//申请理由
    "applyType": "string",//申请类型（4-API调用）（/dim/apiApplyType）
    "concurrent": 0, //并发量
    "description": "string",//描述
    "exportFields": "string",//输出字段(用户描述输出字段)
    "exportType": "string",//输出是否涉密（/dim/exportType）
    "otherRequire": "string",//其它筛选条件(用户描述筛选条件或选择筛选条件)
    "reviewStatus": "0",//审核状态（/dim/reviewStatus）
    //使用频率
    "useFrequency": 0
  }
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "更新成功",
    "code": 0,
    "data": true
}
```

### 审核API申请

> **POST  /apiApply/review/{apiOrderId}**
> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)
* [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **请求参数**

```json
{
  "reviewStatus": "2",//审核状态（/dim/reviewStatus）
  "remark": "审核通过"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 根据apiOrderId查询API授权协议信息列表

> **GET  /apiAgree/{apiOrderId}/list**
> reviewStatus(0:待审核、1：审核通过、2：驳回)
* [协议审核状态](http://172.20.112.122:8080/mizar/dim/agreeReviewStatus)

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
  "data": [
    {
      "mchntId": "mchnt_0800010000_1512980759863",//商户id
      "agreeName": "协议名称",//协议名称
      "updateTime": 1512446854000,
      "createTime": 1512446854000,
      "appId": "application_0800010000_1512446853893",
      "agreeFilePath": "E:/springUpload/1512446853878dwbdpdb.sql",
      "applyApiId": "api_1_1512980759863",
      "agreeId": "agree_api_0800010000_1512446853893",
      "reviewUserId": "yjy1",
      "reviewUserName": "yjy11(技术开发中心)",
      "reviewInstName": "上海信息中心",
      "reviewInstId": "0800010000",                                      "reviewStatus": "1",//协议审核状态（/dim/agreeReviewStatus）
      "remark": "审核描述",
      "apiOrderId": "1"
    }
  ],
  "code": 0,
  "succ": true,
  "msg": null
}
```

### 根据主键查询API授权协议信息

> **GET  /apiAgree/{agreeId}/{apiOrderId}/detail**
> reviewStatus(0:待审核、1：审核通过、2：驳回)
* [协议审核状态](http://172.20.112.122:8080/mizar/dim/agreeReviewStatus)

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
  "data": {
      "mchntId": "mchnt_0800010000_1512980759863",//商户id
      "agreeName": "协议名称",//协议名称
      "updateTime": 1512446854000,
      "createTime": 1512446854000,
      "appId": "application_0800010000_1512446853893",
      "agreeFilePath": "E:/springUpload/1512446853878dwbdpdb.sql",
      "applyApiId": "api_1_1512980759863",
      "agreeId": "agree_api_0800010000_1512446853893",
      "reviewUserId": "yjy1",
      "reviewUserName": "yjy11(技术开发中心)",
      "reviewInstName": "上海信息中心",
      "reviewInstId": "0800010000",                                      "reviewStatus": "1",//协议审核状态（/dim/agreeReviewStatus）
      "remark": "审核描述",
      "apiOrderId": "1"
  },
  "code": 0,
  "succ": true,
  "msg": "ok"
}
```

### 创建API授权协议信息

> **POST  /apiAgree/add**

!> 注：form表单提交,需要上传文件

> **请求参数**

```json
{
    "mchntId": "mchnt_0800010000_1512447381043",//从主表取
    "appId": "application_0800010000_1512446853893",//从主表取
    "applyApiId": "api_2_1512447381043",//从主表取
    "apiOrderId": "Api_0800010000_1512447381043",  //从主表取
    "agreeName": "协议名称",
    "agreeFile": "/path"//协议文件上传
  }
```

> **返回结果**

```json
{
  "data": true,
  "code": 0,
  "succ": true,
  "msg": "ok"
}
```

### 删除API授权协议信息

> **POST  /apiAgree/delete/{agreeId}/{apiOrderId}**

---

> **请求参数**

```json
 {}
```

> **返回结果**

```json
{
  "data": true,
  "code": 0,
  "succ": true,
  "msg": "删除成功"
}
```

### 更新API授权协议信息

> **POST  /apiAgree/update/{agreeId}/{apiOrderId}**

!> 注：form表单提交,需要上传文件

> **请求参数**

```json
{
    "agreeName": "协议名称",
    "agreeFile": "/path"//需要上传文件
  }
```

> **返回结果**

```json
{
  "data":true,
  "code": 0,
  "succ": true,
  "msg": "ok"
}
```

### 审核API授权协议信息

> **POST  /apiAgree/review/{agreeId}/{apiOrderId}**

!> reviewStatus(0:待审核、1：审核通过、2：驳回)
</br> [审核状态](http://172.20.112.122:8080/mizar/dim/agreeReviewStatus)

> **请求参数**

```json
{
  "reviewStatus": "2",//协议审核状态（/dim/agreeReviewStatus）
  "remark": "审核通过"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

## 公共数据敏感字段相关接口

### 查询公共数据敏感字段信息

> **GET  /sensitDataApply/list?pageNo=1&pageSize=10**
* [申请类型](http://172.20.112.122:8080/mizar/dim/sensitApplyType) [字段权限](http://172.20.112.122:8080/mizar/dim/fieldAuth) [是否上传用户协议](http://172.20.112.122:8080/mizar/dim/agreement) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **返回结果**

```json
{
  "data": {
    "data": [
      {
        "dataOrderId": "data_0800010000_1512960672200",//申请单号*
        "applyType": "2",//申请类型 （/dim/sensitApplyType）
        "applyTypeName": "API调用",//申请类型*
        "description": "3",//单号描述*
        "applyReason": "临时使用",//申请原因*
        "applyInstId": "0800010000",//申请单位*
        "applyUserId": "yjy1",//申请用户*
        "reviewStatus": "3",//审核状态（/dim/reviewStatus）
        "reviewStatusName": "草稿",//审核状态*
        "remark": "3",//审核原因*
        "updateTime": 1511849445000,//创建时间*
        "createTime": 1511849445000,//更新时间*

        "tableName": "default.yjy1_tableName",//表名
        "fieldAuth": "1",//字段权限（/dim/fieldAuth）
        "fieldAuthName": "1",//字段权限
        "agreement": "0",//是否上传用户协议（/dim/agreement）
        "agreementName": "0",//是否上传用户协议
        //申请人信息
        "applyInstName": "上海信息中心",
        "applyUserName": "yjy11(技术开发中心)",
        //审核人信息
        "reviewUserName": "yjy11(技术开发中心)",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海信息中心",
        "reviewUserId": "yjy1"
      }
    ],
    "totalCount": 1,
    "currentPage": 1,
    "pageSize": 10
  },
  "code": 0,
  "succ": true,
  "msg": null
}
```

### 查询公共数据敏感字段详细信息

> **GET  /sensitDataApply/{dataOrderId}/detail**
* [申请类型](http://172.20.112.122:8080/mizar/dim/sensitApplyType) [字段权限](http://172.20.112.122:8080/mizar/dim/fieldAuth) [是否上传用户协议](http://172.20.112.122:8080/mizar/dim/agreement) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **返回结果**

```json
{
  "data": {
        "dataOrderId": "data_0800010000_1512960672200",//单号
        "applyType": "2",//申请类型 （/dim/sensitApplyType）
        "applyTypeName": "2",//申请类型
        "description": "更新描述",//单号描述
        "applyInstid": "0800010000",//申请单位
        "applyUserId": "yjy1",//申请用户
        "reviewStatus": "2",//审核状态（/dim/reviewStatus）
        "reviewStatusName": "2",//审核状态
        "remark": "审核通过",//审核描述
        "updateTime": 1513071817000,//更新时间
        "createTime": 1483200000000,//创建时间
        "tableName": "default.yjy1_tableName",//表名
        "fieldAuth": "1",//字段权限（/dim/fieldAuth）
        "fieldAuthName": "1",//字段权限
        "agreement": "0",//是否上传用户协议（/dim/agreement）
        "agreementName": "0",//是否上传用户协议
        //申请人信息
        "applyInstName": "上海信息中心",
        "applyUserName": "yjy11(技术开发中心)",
        //审核人信息
        "reviewUserName": "yjy11(技术开发中心)",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海信息中心",
        "reviewUserId": "yjy1"
  },
  "code": 0,
  "succ": true,
  "msg": null
}
```

### 创建公共数据敏感字段信息

> **POST  /sensitDataApply/add**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)
</br> [申请类型](http://172.20.112.122:8080/mizar/dim/sensitApplyType)
      [是否上传用户协议](http://172.20.112.122:8080/mizar/dim/agreement)
      [字段权限](http://172.20.112.122:8080/mizar/dim/fieldAuth)
      [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **请求参数**

```json
{
    "applyType": "str",//申请类型(5-敏感字段申请)（/dim/sensitApplyType）
    "description": "str",//用户描述该申请单是用来做什么的
    "applyReason": "str",//申请理由
    "agreement": "str",//是否上传用户协议（/dim/agreement）
    "tableName": "str",//表名
    "fieldAuth": "str",//字段权限（/dim/fieldAuth）
    "reviewStatus": "0"//审核状态（/dim/reviewStatus）
}
```

> **返回结果**

```json
{
  "data":true,
  "code": 0,
  "succ": true,
  "msg": "创建成功"
}
```

### 删除公共数据敏感字段信息

> **POST  /sensitDataApply/delete/{dataOrderId}**
> **请求参数**

```json
{}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "删除成功",
    "code": 0,
    "data": true
}
```

### 更新公共数据敏感字段信息

> **POST  /sensitDataApply/update/{dataOrderId}**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)</br>
[申请类型](http://172.20.112.122:8080/mizar/dim/sensitApplyType) [字段权限](http://172.20.112.122:8080/mizar/dim/fieldAuth) [是否上传用户协议](http://172.20.112.122:8080/mizar/dim/agreement) [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **请求参数**

```json
{
    "applyType": "str",//申请类型(5-敏感字段申请)（/dim/sensitApplyType）
    "description": "str",//用户描述该申请单是用来做什么的
    "applyReason": "str",//申请理由
    "agreement": "str",//是否上传用户协议（/dim/agreement）
    "tableName": "str",//表名
    "fieldAuth": "str",//字段权限//审核状态（/dim/fieldAuth）
    "reviewStatus": "0"//审核状态（/dim/reviewStatus）
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "更新成功",
    "code": 0,
    "data": true
}
```

### 审核公共数据敏感字段申请

> **POST  /sensitDataApply/review/{dataOrderId}**

!> reviewStatus(0:草稿、1：待审核、2：审核通过、3 完成、4 ：驳回)</br>
 [审核状态](http://172.20.112.122:8080/mizar/dim/reviewStatus)

> **请求参数**

```json
{
  "reviewStatus": "2",//审核状态（/dim/reviewStatus）
  "remark": "审核通过"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 根据dataOrderId查询敏感数据授权协议列表

> **GET  /sensitDataAgree/{dataOrderId}/list**

!> reviewStatus(0:待审核、1：审核通过、2：驳回)</br>
 [字段权限](http://172.20.112.122:8080/mizar/dim/fieldAuth)
[协议审核状态](http://172.20.112.122:8080/mizar/dim/agreeReviewStatus)

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
  "data": [
    {
        "agreeId": "agree_data_0800010000_1513071889581",//协议单号
        "dataOrderId": "data_0800010000_1512960781936",//申请单号
        "agreeFilePath": "/1513071889573collection.json",//路径
        "fieldAuth": "1",//字段权限（/dim/fieldAuth）
        "agreeName": "协议名称",//协议名称
        "createTime": 1513071890000,
        "updateTime": 1513073682000,
        //审核人信息
        "reviewUserName": "yjy11(技术开发中心)",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海信息中心",
        "reviewUserId": "yjy1",
        "reviewStatus": "2",//协议审核状态（/dim/agreeReviewStatus）
        "remark": "审核通过"//审核描述
    }
  ],
  "code": 0,
  "succ": true,
  "msg": null
}
```

### 根据主键查询敏感数据授权协议信息

> **GET  /sensitDataAgree/{agreeId}/{dataOrderId}/detail**

!> reviewStatus(0:待审核、1：审核通过、2：驳回)
</br> [字段权限](http://172.20.112.122:8080/mizar/dim/fieldAuth) [协议审核状态](http://172.20.112.122:8080/mizar/dim/agreeReviewStatus)

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
  "data": {
        "agreeId": "agree_data_0800010000_1513071889581",//协议单号
        "dataOrderId": "data_0800010000_1512960781936",//申请单号
        "agreeFilePath": "/1513071889573collection.json",//路径
        "fieldAuth": "1",//字段权限（/dim/fieldAuth）
        "agreeName": "协议名称",//协议名称
        "createTime": 1513071890000,
        "updateTime": 1513073682000,
        //审核人信息
        "reviewUserName": "yjy11(技术开发中心)",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海信息中心",
        "reviewUserId": "yjy1",
        "reviewStatus": "2",//协议审核状态（/dim/agreeReviewStatus）
        "remark": "审核通过"//审核描述
  },
  "code": 0,
  "succ": true,
  "msg": "ok"
}
```

### 创建敏感数据授权协议信息

> **POST  /sensitDataAgree/add**

!> 注：form表单提交,需要上传文件

> **请求参数**

```json
{
    "dataOrderId": "data_0800010000_1512960781936",//从主表取
    "fieldAuth":"1",//字段权限-从主表取
    "agreeName": "协议名称",
    "agreeFile": "/path"//需要上传文件
  }
```

> **返回结果**

```json
{
  "data":true,
  "code": 0,
  "succ": true,
  "msg": "ok"
}
```

### 删除敏感数据授权协议信息

> **POST  /sensitDataAgree/delete/{agreeId}/{dataOrderId}**

---

> **返回结果**

```json
{
  "data": true,
  "code": 0,
  "succ": true,
  "msg": "删除成功"
}
```

### 更新敏感数据授权协议信息

> **POST  /sensitDataAgree/update/{agreeId}/{dataOrderId}**

!> 注：form表单提交,需要上传文件

> **请求参数**

```json
{
    "agreeName": "协议名称",
    "agreeFile": "/path"//需要上传文件
}
```

> **返回结果**

```json
{
  "data":true,
  "code": 0,
  "succ": true,
  "msg": "ok"
}
```

### 审核公共数据授权协议申请

> **POST  /sensitDataAgree/review/{agreeId}/{dataOrderId}**

---

> reviewStatus(0:待审核、1：审核通过、2：驳回)</br>
* [协议审核状态](http://172.20.112.122:8080/mizar/dim/agreeReviewStatus)

> **请求参数**

```json
{
  "reviewStatus": "2",//协议审核状态（/dim/agreeReviewStatus）
  "remark": "审核通过"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

## 资源申请相关接口

### 查询资源申请信息

> **GET  /resource/apply/query?reviewStatus=""&pageNo=1&pageSize=10**

!> 注：reviewStatus（0-草稿、1-提交、2-初审通过、3-完成、4-未通过）
> **返回结果**

```json
{
    "data": {
      "data": [{
        "description": "dfsfa",
        "reviewUserName": "大哥",
        "reviewInstId": "0800010000",
        "reviewInstName": "上海一部",
        "applyUserId": "yjy1",
        "resourceOrderId": "Resource_0800010000_1511940352791",
        "applyInstid": "0800010000",
        "reviewStatus": "2",
        "applyReason": "fsdfsf",
        "otherRequire": "545",
        "reviewUserId": "yjy1",
        "createTime": 1511973648000,
        "updateTime": 1512031410000,
        "cpu": 2,
        "memory": 2,
        "remark": "dfsdfs",
        "queueNum": 2,
        "storage": 2,
        "applyType": "1",
        "applyUserName": "大哥",
        "applyInstName": "上海一部"
      }],
      "currentPage": 1,
      "totalCount": 5,
      "pageSize": 10
    },
  "msg": null,
  "succ": true,
  "code": 0
}
```

### 新增资源申请信息

> **POST  /resource/apply/add**

!> 注：reviewStatus（0-草稿、1-提交、2-初审通过、3-完成、4-未通过）
       applyType（1-云平台、2-数据厨房、3-Hbase资源）

> **请求参数**

```json
{
  "applyReason": "fsdfsf",
  "applyType": "1",
  "cpu": "2",
  "description": "dfsfa",
  "memory": "2",
  "otherRequire": "545",
  "queueNum": "2",
  "reviewStatus": "0",
  "storage": "2"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 更新资源申请信息

> **POST  /resource/apply/add**

!> 注：reviewStatus（0-草稿、1-提交、2-初审通过、3-完成、4-未通过）
       applyType（1-云平台、2-数据厨房、3-Hbase资源）

> **请求参数**

```json
{
  "resourceOrderId":"Resource_0800010000_1511940352791",
  "applyReason": "fsdfsf",
  "applyType": "1",
  "cpu": "2",
  "description": "dfsfa",
  "memory": "2",
  "otherRequire": "545",
  "queueNum": "2",
  "reviewStatus": "0",
  "storage": "2"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 删除资源申请信息

> **POST  /resource/apply/{resourceOrderId}/delete**

---

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 查询资源队列信息

> **GET  /resource/queue/query?resourceOrderId=""&pageNo=1&pageSize=10**

---

> **返回结果**

```json
{
  "data": {
    "data": [{
      "resourceOrderId": "Resource_0800010000_1511940352791",
      "memory": 2,
      "cpu": 0,
      "storage": 2,
      "queueId": 3,
      "createTime": 1511943199000,
      "updateTime": 1511956983000
    }],
    "pageSize": 2147483647,
    "currentPage": 1,
    "totalCount": 5
  },
  "succ": true,
  "msg": null,
  "code": 0
}
```

### 新增资源队列信息

> **POST  /resource/queue/add**

---

> **请求参数**

```json
{
  "cpu": "2",
  "memory": "2",
  "queueNum": "2",
  "resourceOrderId": "Resource_0800010000_1511940352791",
  "storage": "2"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 更新资源队列信息

> **POST  /resource/queue/update**

---

> **请求参数**

```json
{
  "cpu": "0",
  "memory": "2",
  "queueId": "3",
  "queueNum": "2",
  "storage": "2"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 删除资源队列信息

> **POST  /resource/queue/{queueId}/delete**

---

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 查询资源队列用户关系信息

> **GET  /resource/queue/user/query?resourceOrderId=""&queueId=""&pageNo=1&pageSize=10**

---

> **返回结果**

```json
{
  "data": {
    "data": [{
      "updateTime": 1511981304000,
      "createTime": 1511981304000,
      "resourceOrderId": "Resource_0800010000_1511940352791",
      "instId": "0800010000",
      "userId": "yjy1",
      "queueId": 3
    }],
    "totalCount": 1,
    "pageSize": 2147483647,
    "currentPage": 1
  },
  "succ": true,
  "msg": null,
  "code": 0
}
```

### 新增资源队列用户映射信息

> **POST  /resource/queue/user/add**

---

> **请求参数**

```json
{
  "queueId": 3,
  "resourceOrderId": "Resource_0800010000_1511940352791",
  "userInfos": [{
    "instId": "888",
    "userId": "333"
  },
  {
    "instId": "666",
    "userId": "999"
  }]
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 更新资源队列用户关系信息

> **POST  /resource/queue/user/update**

---

> **请求参数**

```json
{
  "queueId": 3,
  "resourceOrderId": "Resource_0800010000_1511940352791",
  "userInfos": [{
    "instId": "888",
    "userId": "333"
  },
  {
    "instId": "666",
    "userId": "999"
  }]
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 删除资源队列用户信息

> **POST  /resource/queue/user/delete**

---

> **请求参数**

```json
{
"resourceOrderId":"Resource_0800010000_1511940352791",
"queueId":"3"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 审核资源申请信息

> **POST  /resource/apply/review**

!> 注：reviewStatus（0-草稿、1-提交、2-初审通过、3-完成、4-未通过）

> **请求参数**

```json
{
    "resourceOrderId":"Resource_0800010000_1511940352791",
  "reviewStatus": "2",
  "remark": "dsdsd"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 查询资源申请文件信息

> **GET  /resource/file/query?relationId=""&queueId=""&pageNo=1&pageSize=10**

!> 注：relationId为资源订单ID

> **返回结果**

```json
{
  "data": {
    "data": [{
      "fileName": "dfsad",
      "createTime": 1511974192000,
      "updateTime": 1511974192000,
      "fileDesc": "dsfas",
      "relationType": "1",
      "filePath": "dfsadf",
      "fileId": "12212",
      "fileExt": "dd",
      "relationId": "Resource_0800010000_1511940352791",
      "instId": "sfes",
      "userId": "dfsd"
    }],
    "totalCount": 1,
    "pageSize": 2147483647,
    "currentPage": 1
  },
  "msg": null,
  "succ": true,
  "code": 0
}
```

### 单文件上传资源申请文件信息

> **POST  /resource/file/upload**

---

> **请求参数**

```json
{
  "fileId": "0544",
  "file":"dd.doc",
  "fileDesc": "2dfsdf"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 下载资源申请文件信息

> **GET/resource/file/{fileId}/download**

---

> **返回结果**

## 文件流

### 更新资源申请文件信息

> **POST  /resource/file/update**

---

> **请求参数**

```json
{
  "fileId": "0544",
  "fileDesc": "2dfsdf"
}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```

### 删除资源申请文件信息

> **POST  /resource/file/{fileId}/delete**

---

> **请求参数**

```json
{}
```

> **返回结果**

```json
{
    "succ": true,
    "msg": "操作成功",
    "code": 0,
    "data": true
}
```
