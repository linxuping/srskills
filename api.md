### 1 生成活动 
**POST**
** URL ** /sr/activity/add

**参数**
```json
{
	"openid":"abc",
	"type":"0-课程;1-活动",
	"title":"云南亲子一日游",
	"time_sign_end":"2016-12-13",
	"price":12.3,
	"quantities":20,
	"classes_str":"舞蹈男班\n课程时间\r\n舞蹈男班\n课程时间",
	"activities_str":"费用名称\n价格\n人数限制\r\n费用名称\n价格\n人数限制"
}
```
**返回**
```json
{
	"errcode": 0,
	"errmsg": ""
}
```

### 2. 活动报名
**POST**
**URL** /sr/activity/sign

**参数**
```json
{
	"openid": "openid",
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

### 3. 报名列表 - 点击跳详情
**GET**
**URL** /sr/signup/list?openid=***

**返回**
```json
{
	"data":{
		"infos": [
			{
				"uid": 3,
				"name": "abc",
				"phone": "1234",
				"age": 4,
				"gentle": "male",
				"title": "til",
				"tag": "tag",
				"record": "rec",
			}
		],
		"count":3
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 4. 标签列表
**GET**
**URL** /sr/tag/list?openid=abc

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

### 5. 发布列表
**GET**
**URL** /sr/class/list?openid=abc

**返回**
```json
{
	"data":{
		"classes": [
			{
				"id":2,
				"title":"tile",
				"createtime":"20161201"
			}
		]
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 5. 发布列表
**GET**
**URL** /sr/class/list?openid=abc

**返回**
```json
{
	"data":{
		"activities": [
			{
				"id":2,
				"type":0,
				"title":"tile",
				"createtime":"20161201"
			}
		]
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 6. 详情
**GET**
**URL** /sr/activity/details?openid=abc&actid=2

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
				"title":"舞蹈男班",
				"time":"课程时间"
			}
		],
		"activities":[
			{
				"title":"费用名称",
				"price":"价格",
				"quantities":"人数限制"
			}
		],
		"statistics":{
			"count_signup":10,
			"count_view":29,
			"count_transfer":3
		}
	},
	"errcode": 0,
	"errmsg": ""
}
```

### 7. 修改
**POST**
** URL ** /sr/activity/add

### 8. 更新标签
**POST**
**URL** /sr/tag/update

**参数**
```json
{
	"openid": "openid",
	"actid": 3,
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

### 8. 更新标签
**POST**
**URL** /sr/tag/update

**参数**
```json
{
	"openid": "openid",
	"actid": 3,
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

