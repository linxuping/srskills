### 1 生成活动 
**POST**
** URL ** /sr/activity/add

**参数**
```json
{
	"uid":"abc",
	"type":"0-课程;1-活动",
	"title":"云南亲子一日游",
	"time_from":"活动开始时间",
	"time_to":"活动结束时间",
	"time_sign_end":"2016-12-13",
	"price":12.3,
	"quantities":20,
	"class_options":[
		{
			"title": "舞蹈男班",
			"weekend": "星期(前端判断)",
			"time": "开课时间"
		}
	],
	"activity_options":[
		{
			"title":"费用名称",
			"price":12.9,
			"quantities":20
		}
	]
}
```
**返回**
```json
{
	"errcode": 1,
	"errmsg": "标题已经被使用，请重新输入！"
}
```

### 2. 活动报名
**POST**
**URL** /sr/activity/sign

**参数**
```json
{
	"uid": "uid",
	"name": "家长姓名",
	"phone": "手机",
	"age": "儿童年龄",
	"actid": "活动id",
	"location": "报名时所处位置",
	"option_ids": "1,3,5"
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

--------

### 3. 报名列表 - 点击跳详情
**GET**
**URL** /sr/signup/list?uid=2&page=1&pagesize=3  (指定活动报名列表增加actid=2)

**返回**
```json
{
	"data":{
		"items": [
			{
				"uid": 3,
				"actid": 2,
				"signid": 4,
				"time": 123456789,
				"name": "abc",
				"phone": "1234",
				"age": 4,
				"gender": "male",
				"title": "til",
				"status": "已报名",
				"tag": "tag",
				"record": "rec",
				"signup_url": "https://bbb",
				"signup_url_qrcode": "https://aaa.png"
			}
		],
		"pageable": {
			"page": 0,
			"total": 1
		 }
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 4. 标签列表
**GET**
**URL** /sr/tag/list?uid=abc

**返回**
```json
{
	"data":{
		"tags": [
			"a","b","c"
		]
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 5. 更新标签
**POST**
**URL** /sr/tag/update

**参数**
```json
{
	"uid": "uid",
	"signid": 3,
	"tag": "dd"
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

### 6. 更新记录
**POST**
**URL** /sr/record/update

**参数**
```json
{
	"uid": "uid",
	"signid": 3,
	"record": "dd"
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

--------

### 7. 发布列表
**GET**
**URL** /sr/class/list?uid=abc

**返回**
```json
{
	"data":{
		"classes": [
			{
				"actid":2,
				"type": "课程",
				"status": 1,
				"title":"tile",
				"img_cover":"img",
				"createtime":"20161201",
				"count_signup":10,
				"count_view":29,
				"count_transfer":3,
				"signed":1
			}
		],
		"pageable": {
			"page": 0,
			"total": 1
		 }
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 7.1. 活动统计数据
**GET**
**URL** /sr/class/stat?uid=abc&actid=123

**返回**
```json
{
	"data":{
		"count_signup":10,
		"count_view":29,
		"count_transfer":3
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 8. 详情
**GET**
**URL** /sr/activity/details?uid=abc&actid=2

**返回**
```json
{
	"data":{
		"type":"0-课程;1-活动",
		"title":"云南亲子一日游",
		"time_sign_end":"2016-12-13",
		"price":12.3,
		"quantities":20,
		"classes":[	
			{
				"id": 2,
				"title":"舞蹈男班",
				"time":"课程时间"
			}
		],
		"activities":[
			{
				"id": 3,
				"title":"费用名称",
				"price":"价格",
				"quantities":"人数限制"
			}
		]
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 9. 修改
**POST**
** URL ** /sr/activity/update

**参数**
```json
{
	"actid": 221,
	"uid":"abc",
	"type":"0-课程;1-活动",
	"title":"云南亲子一日游",
	"time_from":"活动开始时间",
	"time_to":"活动结束时间",
	"time_sign_end":"2016-12-13",
	"price":12.3,
	"quantities":20,
	"class_options":[
		{
			"id": 2,
			"title": "舞蹈男班",
			"weekend": "星期(前端判断)",
			"time": "开课时间"
		}
	],
	"activity_options":[
		{
			"id": 3,
			"title":"费用名称",
			"price":12.9,
			"quantities":20
		}
	]
}
```

### 9.1. 消息列表
**GET**
**URL** /sr/signup/msgs?uid=abc&page=1&pagesize=100

**返回**
```json
{
	"data": {
		"msgs": [
			{
				"title":"a",
				"status":"b",
				"createtime":"",
				"name":"jim",
				"signid": 3
			}
		],		
		"pageable": {
			"page": 0,
			"total": 1
		 }
	},
	"errcode": 0,
	"errmsg": ""
}
```


### 9.2. 报名详情
**GET**
**URL** /sr/signup/details?signid=1023&uid=123

**返回**
```json
{
	"data": {
		"name_pa": "a",
		"time": "20151010",
		"phone": "12312312312",
		"name_ch": "child",
		"age": 3,
		"gender": "male",
		"type": "0-课程 1-活动",
		"option": {
			"id": 1,
			"title": "meishu",
			"time_str": "aa-bb cc",
			"price": 2.9,
			"quantities":30
		},
		"tag": "tag",
		"record": "rec"
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 9.3. 获取导出列表文件
**GET**
**URL** /sr/signup/filepath??uid=2

**返回**
```json
{
	"data": {
		"filepath": "http://aaa/bbb.csv"
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 9.4. 关闭报名
**POST**
**URL** /sr/signup/cancel

**参数**
```json
{
	"uid": "uid",
	"actid": 3
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

### 9.5. 恢复报名
**POST**
**URL** /sr/signup/recover

**参数**
```json
{
	"uid": "uid",
	"actid": 3
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

### 9.4. 获取报名二维码
**GET**
**URL** /sr/signup/qrcode??uid=2&actid=3

**返回**
```json
{
	"data": {
		"qrcode": "http://aaa/bbb"
	},
	"errcode": 0,
	"errmsg": ""
}
```

--------

### 10. 我的收益
**GET**
**URL** /sr/income/details?uid=abc

**返回**
```json
{
	"data":{
		"fee_can_extract": 100,
		"fee_settled": 200,
		"fee_will_settle: 300
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 11. 现金提取
**POST**
**URL** /sr/income/extract

**参数**
```json
{
	"uid": "uid",
	"cash_fee_all": 100,
	"cash_fee_extract": 50,
	"name": "test",
	"bank": "zhaohang",
	"account": "123456",
	"record": "dd"
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

### 12. 提取记录
**GET**
**URL** /sr/income/logs?uid=abc&page=1&pagesize=4

**返回**
```json
{
	"data":{
		"logs": [
			{
				"time": "20161212",
				"cash_fee_extract": 100,
				"poundage": 2,
				"cash_fee_result": 98
				"name": "test",
				"bank": "zhaohang",
				"account": "123456",
				"status": "受理中"
			}
		]
	},
	"pageable": {
			"page": 0,
			"total": 1
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 13. 资金流水
**GET**
**URL** /sr/income/flow?uid=abc&page=1&pagesize=4

**返回**
```json
{
	"data":{
		"logs": [
			{
				"time": "20161212",
				"type": "提现、交易、退款",
				"fee": 2,
				"remian": 60
			}
		]
	},
	"pageable": {
			"page": 0,
			"total": 1
	},
	"errcode": 0,
	"errmsg": ""
}
```


