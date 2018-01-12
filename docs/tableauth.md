# 表权限管理相关

## 获取公有表字段权限

> **GET  /sourcetable/auth/public/field**

---

> **params**

```javascript
{
    "dbName": string,
    "tableName": string,
    "userId": string,
    "instId": string,
    "uid": string
}
```

> **返回结果**

```javascript
arr
{
    "name": string;
    "desc": string;
    "type": string;
    "active": boolean;
}
```

## 获取私有表权限

> **GET  /sourcetable/auth/private/field**

---

> **params**

```javascript
{
    "dbName": string,
    "tableName": string,
     "userId": string,
    "instId": string,
    "uid": string
}
```

> **返回结果**

```javascript
arr
{
    "name": string; // R W ALL
    "desc": string;
    "active": boolean;
}
```

## 更新用户的私有表权限

> **POST /sourcetable/users/auth/private/update**

---

> **params**

```javascript
{
    "dbName": string;
    "tableName": string;
    "userId": string;
    "instId": string;
    "uid": string;
    "auths": ["R", "W", "ALL"]
}
```

> **返回结果: Status**

## 更新用户的公有表权限

> **POST /sourcetable/users/auth/public/update**

---

> **params**

```javascript
{
    "dbName": string;
    "tableName": string;
    "userId": string;
    "instId": string;
    "uid": string;
    "auths": ["avc", "asdlmk", "asdsad"];
}
```

> **返回结果: Status**