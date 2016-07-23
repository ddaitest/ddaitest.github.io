---
layout: post
title: "My Android"
description: ""
tags: [DD]
---
{% include JB/setup %}

#API
##app.worker.customers
客户列表
客户留言里取客户列表

###Request

|参数名称|数据类型	|是否必填项	|说明|
|----|-----|----|----|
|ucode	|string	|是	|用户id密文|
|cus_status	|int	|否	|0 默认值，取全部1 取正在进行中的客户2 取已完成的客户|


###Response

|参数名称		|数据类型	|说明|
|-|-|-|
|result			|int		|	执行结果：1成功 0失败|
|data			|object		|返回的数据主体|
|message		|	string	|	result为0时，返回错误信息|

####data：

|参数名称	|数据类型	|说明|
|-|-|-|
|userinfo		|object		|用户信息(当前用户)|
|friends		|list|	联系人列表|
####userinfo：

|参数名称	|数据类型	|说明|
|-|-|-|
|userid			|string		|客户userid|
|picurl			|string		|头像地址|
|name			|string		|名称|
|devicetoken	|	string	|	设备token|

####friends：

|参数名称	|数据类型	|说明|
|-|-|-|
|userid			|string		|客户userid|
|picurl			|string		|头像地址|
|cus_name		|string		|客户名称|
|cus_tel		|string	|	客户电话(对话页需要用)|
|house_addr		|string		|楼盘地址|
|is_finished	|int		|	1进行中的客户2已完成的客户|
|devicetoken	|string	|	设备token|

######Example

```
{
	"result": 1,
	"data": {
		"userinfo": {
			"userid": "c1243",
			"picurl": "http:\/\/bjcache.house.sina.com.cn\/gongzhang\/Chief\/0b\/21\/02c6adcf598fa6f7345daa2ea930_thumb_120x120.jpg",
			"name": "baorui",
			"devicetoken": ""
		},
		"friends": [{
			"userid": "o6",
			"picurl": "http:\/\/bjcache.house.sina.com.cn\/gongzhang\/work_att\/24\/02\/d8128762ad319656ef70b46a16dd.jpg",
			"cus_name": "\u5305\u745e",
			"cus_tel": "18610211532",
			"house_addr": "\u5149\u534e\u8def\u9633\u5149100",
			"is_finished": "1",
			"devicetoken": "",
			"message": "\u5411\u5305\u745e\u53d1\u9001\u4e00\u6761\u6d88\u606f\u3002",
			"time": "\u4e0a\u5348 09:47"
		}]
	},
	"message": ""
}
```


