# 临时接口

## 机构相关

### 获取机构列表

> **POST  /inst/list**

!> [机构列表](http://172.20.112.122:80/inst/list)

> **返回结果**

```json
{
    "succ": true,
    "code": 0,
    "msg": null,
    "data": [
        {
            "instId": "0800010000",
            "instName": "上海信息中心",
            "rootInstId": "0800010000",
            "rootInstName": "上海信息中心"
        }
    ]
}
```

!> 一段重要的内容，可以和其他 **Markdown** 语法混用。

?> *TODO* 完善示例

[link](/)

## BUG修复

### 群管理


```sql
alter table tbl_bdp_fe_group_info add column group_desc varchar(64) not null DEFAULT '' COMMENT '群描述';
```

1. 群管理添加群描述字段.
1. 群管理支持群名称和群描述模糊搜索
1. 修复数据库查询以平台返回数据库为主

## 需求改动

* API申请
* [x] 根据【API类型】联动显示【API功能类型】下拉 -左刚举、方宇卿
* [x] 删除【商户名称】-左刚举、方宇卿
* [ ] 协议列表新建按钮删除掉 -方宇卿
* [ ] 上传协议限制上传类型（doc,docx,xls,xlsx,ppt,pptx,pdf,jpg,jpeg,bmp）-左刚举、方宇卿
* [x] 并发量和使用频率限制只能输入数字并且添加单位提示 -左刚举、方宇卿
* [x] 审核不修改更新时间 -左刚举

* 敏感字段申请
* [ ] 敏感字段申请协议列表前面的选中框去掉 -刘新亚
* 协议文件上传模版
* [ ] 协议文件最大可上传：${SystemParm.AGREE_UPLAOD_SIZE/1024/1024}M,可上传文件类型为：${SystemParm.AGREE_UPLAOD_SUFFIX}