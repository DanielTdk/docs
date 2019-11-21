## API地址
**短连接地址**    
https://www.kongyintianxia.com  
**websocket地址**  
wss://www.kongyintianxia.com
## 限频规则
    行情api 10秒100次；
## 签名验证
* API KEY及SECRET KEY；
* 发起请求
* 签名
* 时间戳
* 获取服务器时间

**API Key 及API secret**  
请联系工作人员获取。

**发起请求**

所有请求头部(header)必须包含如下内容  
COINDOM-ACCESS-KEY 字符串类型的API Key。  
COINDOM-ACCESS-SIGN 使用base64编码签名(请参阅签名)。  
COINDOM-ACCESS-TIMESTAMP 发起请求的时间戳。  
所有请求都应该含有application/json类型内容，并且是有效的JSON

**签名**

COINDOM-ACCESS-SIGN 签名过程如下：

*  排序

获取所有请求参数，不包括字节类型参数，如文件、字节流，剔除值为空的参数，并按照第一个字符的键值ASCII码递增排序（字母升序排序），如果遇到相同字符则按照第二个字符的键值ASCII码递增排序，以此类推。

*  拼接

将排序后的参数与其对应值，组合成“参数=参数值”的格式，并且把这些参数用&字符连接起来，再拼接上&timestamp=<COINDOM-ACCESS-TIMESTAMP>&api_secret=<API secret>，此时生成的字符串为待签名字符串。

*  MD5签名

对第二步所得待签名字符串进行MD5，即得到签名字符串。

**时间戳**

COINDOM-ACCESS-TIMESTAMP请求头必须是UTC时区Unix时间戳的十进制秒数格式或ISO8601标准的时间格式，精确到毫秒

时间戳和服务器时间前后相差30秒以上的请求将被系统视为过期并拒绝。如果您认为服务器和API服务器之间存在较大的时间偏差，那么我们建议您使用获取服务器时间的接口来查询API服务器时间