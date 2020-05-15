## Skill接口
### URI

```
/ai/skill
```

### 请求参数定义

```json
{
  "header":{
  },
  "payload":{
    "profile"      : {
        "mainMode" : string  // 当前设备处于的模式（儿童模式：CHLIDREN 正常模式：NORMAL或者空）， 
    },
    "domain"       : string  // 请求领域, 联合intent用以路由到具体能力
    "intent"       : string  // 请求意图, 联合domain用以路由到具体能力
    "jsonBlobData" : string  // 请求数据, 根据domain,intent，结构有所不同
  }
}
```

### 响应数据定义

```json
payload:
{
   "jsonBlobData": string // 返回数据
   "retCode":0,
   "errMsg":"string"
}
```

### 请求数据示例

```json
{
  "header":{
    "qua":{
      "env":"sandbox"
    }
  },
  "payload":{
    "domain":"domain_common_business",
    "intent":"intent_report_terminate_cost_time",
    "jsonBlobData":"{operType:\"下一首\"，pushInfo:\"xx\"}",
    "retCode":0,
    "errMsg":""
  }
}
```

### 响应数据示例

上报成功，header.code = 200

```
{
  "header":{
    "code":200,
    "message":"",
    "sessionId":"1582034836475758_yVpFMeaGmLIfO"
  },
  "payload":{
    "jsonBlobData":""
  }
}
```

上报失败，header.code != 200

```json
{
  "header":{
    "code":406,
    "message":"xxx",
    "sessionId":"1582178870880332_UyA7xAwkaaUKU"
  },
  "payload":{
    "jsonBlobData":""
  }
}
```