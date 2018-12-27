
# Description: 用户空间——文件操作
## 用户空间文件删除
**URL:** http://{server}/file/rm

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
path|string|    路径|false
rootType|string|根路径类型|false


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
	"msg":"abg8s3",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文档上传
**URL:** http://{server}/file/upload

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
path|string|    路径|false
file|object|    文件对象|true
rootType|string|根路径类型|false


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
	"msg":"rop2kh",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 查询用户空间列表
**URL:** http://{server}/file/docList

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|根路径类型|false
path|string|    路径|false


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
	"msg":"s3ghbl",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 查看用户空间文件内容
**URL:** http://{server}/file/read

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|根路径类型|false
path|string|    路径|false
start|int|   文件起始行|true
limit|int|   读取行数|true


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
	"msg":"tc599q",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文档保存
**URL:** http://{server}/file/save

**Type:** POST

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|No comments found.|false
rootType|string|No comments found.|false
path|string|No comments found.|false
path|string|No comments found.|false
contentBody|map|No comments found.|true
contentBody|map|No comments found.|true


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
	"msg":"jsngkt",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 修改用户空间文件名称
**URL:** http://{server}/file/rename

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
path|string|    路径|false
rootType|string|根路径类型|false
newName|string| 文件名|true


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
	"msg":"fpvkt8",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文件创建
**URL:** http://{server}/file/create

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
path|string|    路径|false
rootType|string|根路径类型|false
type|int|    文件类型|true


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
	"msg":"nqa0jl",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文件删除
**URL:** http://{server}/file/delete

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|根路径类型|false
path|string|    路径|false


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
	"msg":"eq4xak",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 获取文件集合
**URL:** http://{server}/file/getFilesNameList

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|根路径类型|false
path|string|    路径|false
queryStr|string|匹配名|false


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
	"msg":"kdxvgf",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 下载文件
**URL:** http://{server}/file/download

**Type:** GET

**Content-Type:** application/x-www-form-urlencoded


**Request-parameters:**

Parameter | Type|Description|Required
---|---|---|---
rootType|string|根路径type|false
path|string|    路径 文件保存的相对路径  全路径为：用户根目录（后台获取）+相对路径|false


**Request-example:**
```
No Request-example
```
**Response-fields:**

Field | Type|Description
---|---|---
no param name|string|The interface directly returns the string type value.


**Response-example:**
```
"rsbevh"
```

