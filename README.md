## 常用JS正则：
***

#### 1、匹配 6-10 位 数字和字母结合（不能单独字母或者数字）
```javascript
/^(?!([a-zA-Z]+|\d+)$)[a-zA-Z\d]{6,10}$/
```

#### 2、简单的邮件格式
```javascript
/^\w+@\w+.\w+$/
```
```javascript
/([\w\-]+\@[\w\-]+\.[\w\-]+)/
```

#### 3、 目标字符串：\<SPAN style="FONT-FAMILY: 宋体; BACKGROUND: white; COLOR: #333333; FONT-SIZE: 12px; mso-ascii-font-family: simsun; mso-hansi-font-family: simsun; mso-bidi-font-family: 宋体; mso-font-kerning: 0">想要的内容\</SPAN>
结果：想要的内容
```javascript
<SPAN style.*?>(.+)</SPAN>
```
    
#### 4、0到1600之间的正整数的正则表达式（包括0和1600）
```javascript
\b(0|[1-9][0-9]|[1-9][0-9]{2}|1[0-5][0-9]{2}|1600)\b
```

#### 5、【目标字符串】{a:“123\"4\"56789”,b:"45678"}
【想要的匹配结果】123\"4\"56789 45678
```javascript
(?<=:)"(.*?)(?<!\\)"
```

#### 6、2500以上20000以下100的整数倍的正则表达式
不含2W：
```javascript
((2[5-9])|([3-9]\d)|(1\d\d))00
```
含2W：
```javascript
((2[5-9])|([3-9]\d)|(1\d\d)|(200))00
```

#### 7、最后一位必须是英文，其他必须是数字
```javascript
[0-9]+[A-Za-z]$
```

#### 9、检测 URL 地址是否合法
```javascript
/\b(?:(?:https?|ftp):\/\/|www\.)[-a-z0-9+&@#\/%?=~_|!:,.;]*[-a-z0-9+&@#\/%=~_|]/i
```
验证HTTP地址
```javascript
/(http:\/\/|https:\/\/)((\w|=|\?|\.|\/|&|-)+)/g;
```

#### 10、是否只包含字母跟空格
```javascript
/^[a-zA-Z ]*$/
```

#### 11、匹配所有不满11位的数字
var str = \<p>12345600000，12345，456 &nbsp;&nbsp;\</p>\<p>12345699999，12345,11111111111 &nbsp; &nbsp;\</p>\<p>123456 &nbsp; &nbsp;\</p><br>
比如12345、123456 不足11位，匹配里面所有的12345跟123456，但是不匹配12345600000、12345699999、11111111111
```javascript
var reg = new RegExp("("+tmp[j]+")([^0-9])","g");  //tmp[j]是对应的数字
```
```javascript
str.replace(reg,"<font style=\"color:red;\">$1</font>$2"); //$1为组1，$2为组2
```

网上大神的回复：
```javascript
(?<!\d)\d{1,10}(?!\d) 或者 \D(\d{1,10})\D
```


#### 12、匹配图片
```javascript
var pngReg = subject.match(/\/(\w+\.(?:png|jpg|jpeg|gif|bmp))$/i);
```
判断：
```javascript
if(pngReg instanceof Array){}
```


#### 13、判断手机还是平板，或者PC
```javascript
var device = /android|iphone|ipad|ipod|webos|iemobile|opear mini|linux/i.test(navigator.userAgent.toLowerCase());
```