
# Description: 用户空间——文件操作
## 用户空间文件删除
**URL:** null/file/rm

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":657,
	"msg":"ljxd36",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文档上传
**URL:** null/file/upload

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":212,
	"msg":"jni3us",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 查询用户空间列表
**URL:** null/file/docList

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":174,
	"msg":"bllqkp",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 查看用户空间文件内容
**URL:** null/file/read

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":304,
	"msg":"y75qvt",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文档保存
**URL:** null/file/save

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":500,
	"msg":"jpyco3",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 修改用户空间文件名称
**URL:** null/file/rename

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":12,
	"msg":"3s43gs",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文件创建
**URL:** null/file/create

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":157,
	"msg":"albd31",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 用户空间文件删除
**URL:** null/file/delete

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":604,
	"msg":"q0g9fj",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 获取文件集合
**URL:** null/file/getFilesNameList

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
succ|boolean|后台返回给前台的结果
code|int|后台返回给前端的状态码
msg|string|调用失败的时候会给这个字段赋值
data|object|后台给前台返回的数据


**Response-example:**
```
{
	"succ":true,
	"code":838,
	"msg":"1vjok3",
	"data":{
		"waring":"You may have used non-display generics."
	}
}
```

## 下载文件
**URL:** null/file/download

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
"keswbn"
```

