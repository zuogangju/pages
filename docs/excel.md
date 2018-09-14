## 上传excel(表单上传)

***POST请求:*** **/excel/upload**

> **请求参数**

```json
{
    "file": "string"
}
```

> **返回结果**

```json
{
    {"success/error":"uploadsucc/error"}
}
```
## 查询excel上传表单

***GET请求:*** **/excel/list**

> **请求参数**

```json
{
    "page": "int",
    "pageSize": "int",
}
```

> **返回结果**

```json
{
  "data": [
    {
      "dataTime": "string",
      "errorMsg": "string",
      "fileId": "string",
      "fileName": "string",
      "filePath": "string",
      "fileStatus": "string",
      "instId": "string",
      "userId": "string"
    }
  ],
  "page": 0,
  "pageSize": 0,
  "records": 0
}
```
## excel文件下载

***GET请求:*** **/excel/downfile**

> **请求参数**

```json
{
    "fileId": "int"
}
```

> **返回结果**
