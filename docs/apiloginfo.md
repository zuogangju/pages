# api调用日志

## api调用日志查询

***GET请求*** **/apilog/list**

!> [机构](http://172.20.112.122/inst/list)

> **请求参数**

```json
{
    "instId": "string", // 机构下拉
    "requestAppId": "string",
    "createTimeStart": "2018-01-01",
    "createTimeEnd": "2018-01-08"
}
```

> **返回结果**

```json
{
  "succ": true,
  "code": 0,
  "msg": null,
  "data": {
    "totalCount": 16,//修改
    "data": [
      {
        "instId": "0800010000",
        "instName": "上海信息中心",
        "responseMsgTotalSum": 11,//修改
        "responseMsgTotalCount": 1,//修改
        "requestAppId": "application_0800010000_1516087209381"
      }
    ]
  }
}
```
