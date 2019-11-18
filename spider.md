# spider

#### 什么是互联网爬虫？

```
1.通过一个程序，根据Url进行爬取网页，获取有用信息
2.使用程序模拟浏览器，去向服务器发送请求，获取响应信息
```

#### 爬虫核心?

```
1.爬取网页：爬取整个网页  包含了网页中所有得内容
2.解析数据：将网页中你得到的数据 进行解析
3.难点：爬虫和反爬虫之间的博弈
```

#### 爬虫的用途？

- 数据分析/人工数据集
- 社交软件冷启动
- 舆情监控
- 竞争对手监控

#### 爬虫语言分类？

```
1.php:多进程和多线程支持不好
2.java:目前java爬虫需求岗位旺盛，python爬虫的主要对手，代码臃肿，代码量大、重构成本高，而爬虫需要经常修改，所以不好用
3.C\C++:学习成本比较高，性能和效率高，停留在研究层面，市场需求量小。体现程序员能力。
4.python:语法简洁优美、对新手友好，学习成本低、支持的模块非常多、有scrapy非常强大的爬虫框架
```

#### 爬虫分类？

```
通用爬虫：
	实例
		百度、360、google、sougou等搜索引擎---伯乐在线
	功能
		访问网页->抓取数据->数据存储->数据处理->提供检索服务
	robots协议
		一个约定俗成的协议，添加robots.txt文件，来说明本网站哪些内容不可以被抓取，起不到限制作用
		自己写的爬虫无需遵守
	网站排名(SEO)
		1. 根据pagerank算法值进行排名（参考个网站流量、点击率等指标）
		2. 百度竞价排名，钱多就是爸爸
	缺点
		1. 抓取的数据大多是无用的
		2.不能根据用户的需求来精准获取数据
```

```
聚焦爬虫
	功能
		根据需求，实现爬虫程序，抓取需要的数据
	原理
		1.网页都有自己唯一的url(统一资源定位符）
		2.网页都是html组成
		3.传输协议都是http\https
	设计思路
		1.确定要爬取的url
			如何获取Url
		2.模拟浏览器通过http协议访问url，获取服务器返回的html代码
			如何访问
		3.解析html字符串（根据一定规则提取需要的数据）
			如何解析
```

#### 反爬手段？

```
1.User-Agent：
	User Agent中文名为用户代理，简称 UA，它是一个特殊字符串头，使得服务器能够识别客户使用的操作系统及版本、CPU 类型、浏览器及版本、浏览器渲染引擎、浏览器语言、浏览器插件等。
2.代理IP
	西次代理
	快代理
	什么是高匿名、匿名和透明代理？它们有什么区别？
		1.使用透明代理，对方服务器可以知道你使用了代理，并且也知道你的真实IP。
		2.使用匿名代理，对方服务器可以知道你使用了代理，但不知道你的真实IP。
		3.使用高匿名代理，对方服务器不知道你使用了代理，更不知道你的真实IP。
3.验证码访问
	打码平台
      云打码平台
      超级🦅
4.动态加载网页  网站返回的是js数据 并不是网页的真实数据 
	selenium驱动真实的浏览器发送请求
5.数据加密  
	分析js代码
	
爬虫-反爬虫-反反爬虫
```

#### Http协议

```
1.http和https区别？
	http
		明文传输，端口号80
		HTTP协议（HyperText Transfer Protocol，超文本传输协议）：是一种发布和接收 HTML页面的方法。

	https
		加密传输，端口号443
		HTTPS（Hypertext Transfer Protocol over Secure Socket Layer）简单讲是HTTP的安全版，在HTTP下加入SSL层。    HTTPS = HTTP+SSL

		SSL（Secure Sockets Layer 安全 套接层）主要用于Web的安全传输协议，在传输层对网络连接进行加密，保障在Internet上数据传输的安全。
2.什么是SSL？
	SSL
		什么是安全认证
		关于CA
		12306网站证书是自己的
		安全认证requests
		安全认证urllib
	注意：如果报错SSL,那么解决方案是
              import urllib.request
              import ssl
              ssl._create_default_https_context = ssl._create_unverified_context
3.常见服务器端口号
		ftp      21
		ssh      22
		mysql    3306
		oracle   1521
		MongoDB  27017
		redis    6379
	http工作原理
		url组成
			协议	主机   端口号  路径   参数  锚点
		上网原理
		http请求和响应
			请求行.请求头、请求体
			响应行.响应头、响应体
			请求头详解
				Accept
				Accept-Encoding
				Accept-Language
				Cache-Control
				Connection
				Cookie
				Host
				Upgrade-Insecure-Requests    http是否升级为https
				User-Agent 
				X-Requested-With             是否是ajax请求             
				Referer                      上一级路径
			响应头详解
				Connection
				Content-Encoding
				Content-Type
				Date
				Expires
				Server
				Transfer-Encoding            内容是否分包传输
			常见HTTP状态码
				200
					请求成功
				404
					未找到资源
				500
					服务器内部错误
```



#### urllib库使用

```
	urllib.request.urlopen() 模拟浏览器向服务器发送请求
	response    服务器返回的数据
		response的数据类型是HttpResponse
		字节-->字符串
				解码decode
		字符串-->字节
				编码encode
		read()       字节形式读取二进制   扩展：rede(5)返回前几个字节
		readline()   读取一行
		readlines()  一行一行读取 直至结束
		getcode()    获取状态码
		geturl()     获取url
		getheaders() 获取headers
	urllib.request.urlretrieve()
		请求网页
		请求图片
		请求视频
```

```
pycharm代码例子：

import urllib.request
url='http://www.baidu.com'
# 使用urllib访问url路径
response = urllib.request.urlopen(url=url)
# 得到response即使访问路径的响应,可以使用方法读取内容
content = response.read()  
# 需要注意的是，读取的内容是二进制，
# 一般的内容编码都是utf-8 
# 也有自定义编码的网页，根据网页中meta的charset来解码
content = content.decode('utf-8')
# 此时的content就是访问url得到的内容
# 许多网页添加了反扒手段，仅仅使用这些代码并不能得到真正的源码

#使用urllib下载图片，下载视频、音频
url=`src`
# 这里的src是图片或者视频资源的下载路径

urllib.request.urlretrieve(url=url,filename='diy.jpg')
#此时会将路径得到的内容下载到本地，并一filename命名

```



扩展：编码的由来

```
'''编码集的演变---
由于计算机是美国人发明的，因此，最早只有127个字符被编码到计算机里，也就是大小写英文字母、数字和一些符号，
这个编码表被称为ASCII编码，比如大写字母A的编码是65，小写字母z的编码是122，0的编码是48。
但是要处理中文显然一个字节是不够的，至少需要两个字节，而且还不能和ASCII编码冲突，
所以，中国制定了GB2312编码，用来把中文编进去。
你可以想得到的是，全世界有上百种语言，日本把日文编到Shift_JIS里，韩国把韩文编到Euc-kr里，
各国有各国的标准，就会不可避免地出现冲突，结果就是，在多语言混合的文本中，显示出来会有乱码。
因此，Unicode应运而生。Unicode把所有语言都统一到一套编码里，这样就不会再有乱码问题了。
Unicode标准也在不断发展，但最常用的是用两个字节表示一个字符（如果要用到非常偏僻的字符，就需要4个字节）。
现代操作系统和大多数编程语言都直接支持Unicode。'''

```

#### 请求对象的定制

```
UA介绍：User Agent中文名为用户代理，简称 UA，它是一个特殊字符串头，使得服务器能够识别客户使用的操作系统及版本、CPU 类型、浏览器及版本。浏览器内核、浏览器渲染引擎、浏览器语言、浏览器插件等

```

```
语法：request = urllib.request.Request()

```



#### 1编解码

###### 1.get请求方式：urllib.parse.quote（）

```
eg：
import urllib.request
import urllib.parse

url = 'https://www.baidu.com/s?wd='

headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36'
}

url = url + urllib.parse.quote('小野')

request = urllib.request.Request(url=url,headers=headers)

response = urllib.request.urlopen(request)

print(response.read().decode('utf-8'))

```

```
ajax的get请求例子：

import urllib.request 
import urllib.parse

url = 'http://……'

data={
	'kw':'data1',
	'wd':'data2',
}

headers = {
	    'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/78.0.3904.70 Safari/537.36',

}

# 使用urllib.parse进行转码
# quote 进行单个数据转码
# data = urllib.parse.quote('搜索内容') 


```













###### 2.get请求方式：urllib.parse.urlencode（）

```
eg:
import urllib.request
import urllib.parse
url = 'http://www.baidu.com/s?'
data = {
    'name':'小刚',
    'sex':'男',
}
data = urllib.parse.urlencode(data)
url = url + data
print(url)
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36'
}
request = urllib.request.Request(url=url,headers=headers)
response = urllib.request.urlopen(request)
print(response.read().decode('utf-8'))

```

###### 3.post请求方式

```
eg:百度翻译
import urllib.request
import urllib.parse
url = 'https://fanyi.baidu.com/sug'
headers = {
    'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36'
}
keyword = input('请输入您要查询的单词')
data = {
    'kw':keyword
}
data = urllib.parse.urlencode(data).encode('utf-8')
request = urllib.request.Request(url=url,headers=headers,data=data)
response = urllib.request.urlopen(request)
print(response.read().decode('utf-8'))

```

总结：post和get区别？

```
1：get请求方式的参数必须编码，参数是拼接到url后面，编码之后不需要调用encode方法
2：post请求方式的参数必须编码，参数是放在请求对象定制的方法中，编码之后需要调用encode方法

```

案例练习：百度详细翻译

```
import urllib.request
import urllib.parse

url = 'https://fanyi.baidu.com/v2transapi'
headers = {
    # ':authority': 'fanyi.baidu.com',
    # ':method': 'POST',
    # ':path': '/v2transapi',
    # ':scheme': 'https',
    # 'accept': '*/*',
    # 'accept-encoding': 'gzip, deflate, br',
    # 'accept-language': 'zh-CN,zh;q=0.9',
    # 'content-length': '119',
    # 'content-type': 'application/x-www-form-urlencoded; charset=UTF-8',
    'cookie': 'REALTIME_TRANS_SWITCH=1; FANYI_WORD_SWITCH=1; HISTORY_SWITCH=1; SOUND_SPD_SWITCH=1; SOUND_PREFER_SWITCH=1; PSTM=1537097513; BIDUPSID=D96F9A49A8630C54630DD60CE082A55C; BAIDUID=0814C35D13AE23F5EAFA8E0B24D9B436:FG=1; to_lang_often=%5B%7B%22value%22%3A%22en%22%2C%22text%22%3A%22%u82F1%u8BED%22%7D%2C%7B%22value%22%3A%22zh%22%2C%22text%22%3A%22%u4E2D%u6587%22%7D%5D; from_lang_often=%5B%7B%22value%22%3A%22zh%22%2C%22text%22%3A%22%u4E2D%u6587%22%7D%2C%7B%22value%22%3A%22en%22%2C%22text%22%3A%22%u82F1%u8BED%22%7D%5D; BDORZ=B490B5EBF6F3CD402E515D22BCDA1598; delPer=0; H_PS_PSSID=1424_21115_29522_29519_29099_29568_28835_29220_26350; PSINO=2; locale=zh; Hm_lvt_64ecd82404c51e03dc91cb9e8c025574=1563000604,1563334706,1565592510; Hm_lpvt_64ecd82404c51e03dc91cb9e8c025574=1565592510; yjs_js_security_passport=2379b52646498f3b5d216e6b21c6f1c7bf00f062_1565592544_js',
    # 'origin': 'https://fanyi.baidu.com',
    # 'referer': 'https://fanyi.baidu.com/translate?aldtype=16047&query=&keyfrom=baidu&smartresult=dict&lang=auto2zh',
    # 'sec-fetch-mode': 'cors',
    # 'sec-fetch-site': 'same-origin',
    # 'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36',
    # 'x-requested-with': 'XMLHttpRequest',
}
data = {
    'from': 'en',
    'to': 'zh',
    'query': 'you',
    'transtype': 'realtime',
    'simple_means_flag': '3',
    'sign': '269482.65435',
    'token': '2e0f1cb44414248f3a2b49fbad28bbd5',
}
#参数的编码
data = urllib.parse.urlencode(data).encode('utf-8')
# 请求对象的定制
request = urllib.request.Request(url=url,headers=headers,data=data)
response = urllib.request.urlopen(request)
# 请求之后返回的所有的数据
content = response.read().decode('utf-8')
import json
# loads将字符串转换为python对象
obj = json.loads(content)
# python对象转换为json字符串  ensure_ascii=False  忽略字符集编码
s = json.dumps(obj,ensure_ascii=False)
print(s)

```

#### ajax的get请求

案例：豆瓣电影

```
# 爬取豆瓣电影前10页数据
# https://movie.douban.com/j/chart/top_list?type=20&interval_id=100%3A90&action=&start=0&limit=20
# https://movie.douban.com/j/chart/top_list?type=20&interval_id=100%3A90&action=&start=20&limit=20
# https://movie.douban.com/j/chart/top_list?type=20&interval_id=100%3A90&action=&start=40&limit=20

import urllib.request
import urllib.parse

# 下载前10页数据
# 下载的步骤：1.请求对象的定制  2.获取响应的数据 3.下载

# 每执行一次返回一个request对象
def create_request(page):
    base_url = 'https://movie.douban.com/j/chart/top_list?type=20&interval_id=100%3A90&action=&'
    headers = {
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36'
    }
    data={
        #  1 2  3  4
        #  0 20 40 60
        'start':(page-1)*20,
        'limit':20
    }
    # data编码
    data = urllib.parse.urlencode(data)
    url = base_url + data
    request = urllib.request.Request(url=url,headers=headers)
    return request
# 获取网页源码
def get_content(request):
    response = urllib.request.urlopen(request)
    content = response.read().decode('utf-8')
    return content

def down_load(page,content):
#    with open（文件的名字，模式，编码）as fp:
#        fp.write(内容)
    with open('douban_'+str(page)+'.json','w',encoding='utf-8')as fp:
        fp.write(content)

if __name__ == '__main__':
    start_page = int(input('请输入起始页码'))
    end_page = int(input('请输入结束页码'))
    for page in range(start_page,end_page+1):
        request = create_request(page)
        content = get_content(request)
        down_load(page,content)

```

#### ajax的post请求

案例：KFC官网

#### 复杂get

案例：百度贴吧



扩展：CURL（访问服务器获取页面源码）

```
1.查看curl版本
2.curl基本使用
		（1）访问页面 eg：curl http://www.baidu.com
		 (2)携带UA   eg: curl -A 'Chrome' http://www.baidu.com
		 (3)post请求 eg：curl -X POST http://httpbin.org/post

```

### URLError\HTTPError

```
简介:1.HTTPError类是URLError类的子类
     2.导入的包urllib.error.HTTPError    urllib.error.URLError
     3.http错误：http错误是针对浏览器无法连接到服务器而增加出来的错误提示。引导并告诉浏览者该页是哪里出了问题。
     4.通过urllib发送请求的时候，有可能会发送失败，这个时候如果想让你的代码更加的健壮，可以通过try-except进行捕获异常，异常有两类，URLError\HTTPError
```

```
eg:

import urllib.request
import urllib.error

url = 'https://blog.csdn.net/ityard/article/details/102646738'

# url = 'http://www.goudan11111.com'

headers = {
        # 'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3',
        # 'Accept-Encoding': 'gzip, deflate, br',
        # 'Accept-Language': 'zh-CN,zh;q=0.9',
        # 'Cache-Control': 'max-age=0',
        # 'Connection': 'keep-alive',
        'Cookie': 'uuid_tt_dd=10_19284691370-',
        # 'Host': 'blog.csdn.net',
        # 'Referer': 'https://passport.csdn.net/login?code=public',
        # 'Sec-Fetch-Mode': 'navigate',
        # 'Sec-Fetch-Site': 'same-site',
        # 'Sec-Fetch-User': '?1',
        # 'Upgrade-Insecure-Requests': '1',
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/77.0.3865.120 Safari/537.36',
    }
try:
    request = urllib.request.Request(url=url,headers=headers)

    response = urllib.request.urlopen(request)

    content = response.read().decode('utf-8')
    print(content)
except urllib.error.HTTPError:
    print(1111)

except urllib.error.URLError:
    print(2222)

```

### cookie登录

```
使用案例：
        1.人人网登陆
        2.weibo登陆
        作业：qq空间的爬取
在头信息中添加cookie，携带cookie信息
```

### Handler处理器

```
为什么要学习handler？
      urllib.request.urlopen(url)
          不能定制请求头
      urllib.request.Request(url,headers,data)
          可以定制请求头
      Handler
          定制更高级的请求头（随着业务逻辑的复杂 请求对象的定制已经满足不了我们的需求（动态cookie和代理不能使用请求对象的定制）
```

```
eg:
import urllib.request
url = 'http://www.baidu.com'
headers = {
        'User - Agent': 'Mozilla / 5.0(Windows NT 10.0;Win64;x64) AppleWebKit / 537.36(KHTML, likeGecko) Chrome / 74.0.3729.169Safari / 537.36'
    }
request = urllib.request.Request(url=url,headers=headers)

handler = urllib.request.HTTPHandler()

opener = urllib.request.build_opener(handler)

response = opener.open(request)

print(response.read().decode('utf-8'))

```

### 代理服务器

```
1.什么是代理服务器?
	是一种重要的服务器安全功能，它的工作主要在开放系统互联(OSI)模型的会话层，从而起到防火墙的作用
翻墙，是指绕过相应的IP封锁、内容过滤、域名劫持、流量限制等
2.代理的常用功能?
	1.突破自身IP访问限制，访问国外站点。
	2.访问一些单位或团体内部资源
			扩展：某大学FTP(前提是该代理地址在该资源的允许访问范围之内)，使用教育网内地址段免费代理服务器，就可以用于对教育网开放的各类FTP下载上传，以及各类资料查询共享等服务。
	3.提高访问速度
			扩展：通常代理服务器都设置一个较大的硬盘缓冲区，当有外界的信息通过时，同时也将其保存到缓冲区中，当其他用户再访问相同的信息时， 则直接由缓冲区中取出信息，传给用户，以提高访问速度。
	4.隐藏真实IP
			扩展：上网者也可以通过这种方法隐藏自己的IP，免受攻击。
3.代码配置代理
	创建Reuqest对象
	创建ProxyHandler对象
	用handler对象创建opener对象
	使用opener.open函数发送请求
```

```python
eg:
import urllib.request
url = 'http://www.baidu.com/s?wd=ip'
headers = {
	'User - Agent': 'Mozilla / 5.0(Windows NT 10.0;Win64;x64) AppleWebKit / 537.36(KHTML, likeGecko) Chrome / 74.0.3729.169Safari / 537.36',
    'cookie':'dfajhgla',
    }
request = urllib.request.Request(url=url,headers=headers)
proxies = {'http':'117.141.155.244:53281'}
handler = urllib.request.ProxyHandler(proxies=proxies)
opener = urllib.request.build_opener(handler)
response = opener.open(request)
content = response.read().decode('utf-8')
with open('daili.html','w',encoding='utf-8')as fp:
    fp.write(content)
```

扩展：1.代理池，在一个字典中随机选一个

​			2.快代理（网站）



### cookie库

	1.cookie库能干啥:通过handler登陆会自动的保存登录之后的cookie
	2.cookie库配置
		创建一个CookieJar对象
		使用cookiejar对象，创建一个handler对象
		使用handler创建一个opener
		通过opener登录
		handler会自动的保存登录之后的cookie

```python
案例：全书网
# 登陆之后进入到藏书架
import urllib.request
import urllib.parse
import http.cookiejar

url_login = 'http://www.quanshuwang.com/login.php?do=submit'
headers = {
        'User - Agent': 'Mozilla / 5.0(Windows NT 10.0;Win64;x64) AppleWebKit / 537.36(KHTML, likeGecko) Chrome / 74.0.3729.169Safari / 537.36'
    }
data = {
    'username': 'action',
    'password': 'action',
    'action': 'login',
}
# 对参数进行编码
data = urllib.parse.urlencode(data).encode('utf-8')
# 请求对象的定制
request = urllib.request.Request(url=url_login,headers=headers,data=data)
# 获取一个cookiejar对象
cookiejar = http.cookiejar.CookieJar()
# 获取一个handler对象
handler = urllib.request.HTTPCookieProcessor(cookiejar=cookiejar)
# 获取opener对象
opener = urllib.request.build_opener(handler)
# 获取response对象
response = opener.open(request)
url_bookcase = 'http://www.quanshuwang.com/modules/article/bookcase.php'
request_bookcase = urllib.request.Request(url=url_bookcase,headers=headers)
# 因为之前的opener中 已经包含了登陆的cookie  那么再次使用opener 就会携带已经存在cookie
# 去访问了
response_bookcase = opener.open(request_bookcase)
content = response_bookcase.read().decode('gbk')
with open('bookcase.html','w',encoding='gbk')as fp:
    fp.write(content)
```



### xpath

```xpath
xpath基本语法：
	1.路径查询
		//：查找所有子孙节点，不考虑层级关系
		/：找直接子节点
	2.谓词查询
		//div[@id]  
		//div[@id="maincontent"]    
	3.属性查询
		//@class         
	4.模糊查询
		//div[contains(@id, "he")]   
		//div[starts-with(@id, "he")] 
	5.内容查询
		//div/h1/text()
	6.逻辑运算
		//div[@id="head" and @class="s_down"]
		//title | //price
```

```python
xpath使用：
	注意：提前安装xpath插件
	1.安装lxml库      
			pip install lxml -i https://pypi.douban.com/simple
	2.导入lxml.etree  
			from lxml import etree
	3.etree.parse()   解析本地文件
		    html_tree = etree.parse('XX.html')	
	4.etree.HTML()    服务器响应文件
		    html_tree = etree.HTML(response.read().decode('utf-8')	
	4.html_tree.xpath(xpath路径)
```



### JsonPath

```
jsonpath的安装及使用方式：
			pip安装： 
				   pip install jsonpath
			jsonpath的使用：
                    obj = json.load(open('json文件', 'r', encoding='utf-8'))
                    ret = jsonpath.jsonpath(obj, 'jsonpath语法')
```

```
json对象的转换
	json.loads()
		是将字符串转化为python对象
	json.dumps()
		将python对象转化为json格式的字符串
	json.load()
		读取json格式的文本，转化为python对象
		json.load(open(a.json))
	json.dump()
		将python对象写入到文本中
```

教程连接（http://blog.csdn.net/luxideyao/article/details/77802389）

应用案例：智联招聘（薪水，公司名称，职位需求）

作业： 1.股票信息提取（http://quote.stockstar.com/）



### BeautifulSoup

1.基本简介

```
简介：
1.BeautifulSoup简称：
     bs4
2.什么是BeatifulSoup？
	BeautifulSoup，和lxml一样，是一个html的解析器，主要功能也是解析和提取数据
3.优缺点？
	缺点：效率没有lxml的效率高	
	优点：接口设计人性化，使用方便
```

2.安装以及创建

```
1.安装
	pip install bs4
2.导入
	from bs4 import BeautifulSoup
3.创建对象
	服务器响应的文件生成对象
		soup = BeautifulSoup(response.read().decode(), 'lxml')
	本地文件生成对象
		soup = BeautifulSoup(open('1.html'), 'lxml')
		注意：默认打开文件的编码格式gbk所以需要指定打开编码格式
```

3.节点定位

```
1.根据标签名查找节点
		soup.a 【注】只能找到第一个a
			soup.a.name
			soup.a.attrs
2.函数
		(1).find(返回一个对象)
                  find('a')：只找到第一个a标签
                  find('a', title='名字')
                  find('a', class_='名字')
		(2).find_all(返回一个列表)
                  find_all('a')  查找到所有的a
                  find_all(['a', 'span'])  返回所有的a和span
                  find_all('a', limit=2)  只找前两个a
		(3).select(根据选择器得到节点对象)【推荐】
                  1.element
                      eg:p
                  2..class
                      eg:.firstname
                  3.#id
                      eg:#firstname
                  4.属性选择器
                      [attribute]
                          eg:li = soup.select('li[class]')
                      [attribute=value]
                          eg:li = soup.select('li[class="hengheng1"]')
                  5.层级选择器
                      element element
                          div p
                      element>element
                          div>p
                      element,element
                          div,p 
                          		eg:soup = soup.select('a,span')
3.获取子孙节点
		contents：返回的是一个列表
			eg:print(soup.body.contents)
		descendants：返回的是一个生成器
			eg:for a in soup.body.descendants:
					print(a)
```



4.节点信息

```
	(1).获取节点内容：适用于标签中嵌套标签的结构
            obj.string
            obj.get_text()【推荐】
	(2).节点的属性
            tag.name 获取标签名
                eg:tag = find('li)
                   print(tag.name)
		   tag.attrs将属性值作为一个字典返回
	(3).获取节点属性
            obj.attrs.get('title')【常用】
            obj.get('title')
            obj['title']
```

5.节点类型

```
节点类型
	bs4.BeautifulSoup 根节点类型
	bs4.element.NavigableString 连接类型  可执行的字符串
	bs4.element.Tag 节点类型  
	bs4.element.Comment 注释类型
		eg:
			if type(aobj.string) == bs4.element.Comment:
                print('这个是注释内容')
             else:
                print('这不是注释')
```

应用实例： 1.股票信息提取（http://quote.stockstar.com/）

​		    2.中华英才网-旧版

​                    3 .腾讯公司招聘需求抓取（https://hr.tencent.com/index.php）​



### selenium

```
1.什么是selenium？
	（1）Selenium是一个用于Web应用程序测试的工具。
	（2）Selenium 测试直接运行在浏览器中，就像真正的用户在操作一样。
	（3）支持通过各种driver（FirfoxDriver，IternetExplorerDriver，OperaDriver，ChromeDriver）驱动真实浏览器完成测试。
	（4）selenium也是支持无界面浏览器操作的。
```

```
2.为什么使用selenium？
	模拟浏览器功能，自动执行网页中的js代码，实现动态加载
```

```
3.如何安装selenium？
	（1）操作谷歌浏览器驱动下载地址
			http://chromedriver.storage.googleapis.com/index.html 
	（2）谷歌驱动和谷歌浏览器版本之间的映射表
			http://blog.csdn.net/huilan_same/article/details/51896672
	（3）查看谷歌浏览器版本
			谷歌浏览器右上角-->帮助-->关于
	（4）pip install selenium
```

```
4.selenium的使用步骤？
	（1）导入：from selenium import webdriver
	（2）创建谷歌浏览器操作对象：
				path = 谷歌浏览器驱动文件路径
				browser = webdriver.Chrome(path)
	（3）访问网址
				url = 要访问的网址
				browser.get(url)
```

```
4-1：selenium的元素定位？
		元素定位：自动化要做的就是模拟鼠标和键盘来操作来操作这些元素，点击、输入等等。操作这些元素前首先要找到它们，WebDriver提供很多定位元素的方法
		方法：
              1.find_element_by_id
              			eg:button = browser.find_element_by_id('su')
              2.find_elements_by_name
              			eg:name = browser.find_element_by_name('wd')
              3.find_elements_by_xpath
              			eg:xpath1 = browser.find_elements_by_xpath('//input[@id="su"]')
              4.find_elements_by_tag_name
              			eg:names = browser.find_elements_by_tag_name('input')
              5.find_elements_by_css_selector
              			eg:my_input = browser.find_elements_by_css_selector('#kw')[0]
              6.find_elements_by_link_text
              			eg:browser.find_element_by_link_text("新闻")
```

```
4-2:访问元素信息
	获取元素属性
		.get_attribute('class')
	获取元素文本
		.text
	获取id
		.id
	获取标签名
		.tag_name
```

```
4-3:交互
	点击:click()
	输入:send_keys()
	后退操作:browser.back()
	前进操作:browser.forword()
	模拟JS滚动:
		js = 'document.body.scrollTop=100000'
		js='document.documentElement.scrollTop=100000'
		browser.execute_script(js) 执行js代码
	获取网页代码：page_source 
	退出：browser.quit()
	案例练习：糗事百科
```

### Phantomjs

```
1.什么是Phantomjs？
	（1）是一个无界面的浏览器
	（2）支持页面元素查找，js的执行等
	（3）由于不进行css和gui渲染，运行效率要比真实的浏览器要快很多
```

```
2.如何使用Phantomjs？
	（1）获取PhantomJS.exe文件路径path
	（2）browser = webdriver.PhantomJS(path)
	（3）browser.get(url)
	 扩展：保存屏幕快照:browser.save_screenshot('baidu.png')
```

### Chrome handless

```
1.系统要求：
          Chrome 
                Unix\Linux 系统需要 chrome >= 59 
                Windows 系统需要 chrome >= 60
          Python3.6
          Selenium==3.4.*
          ChromeDriver==2.31
```

```
2.配置：
	from selenium import webdriver
	from selenium.webdriver.chrome.options import Options

    chrome_options = Options()
    chrome_options.add_argument('--headless')
    chrome_options.add_argument('--disable-gpu')

    path = r'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe'
    chrome_options.binary_location = path

	browser = webdriver.Chrome(chrome_options=chrome_options)

	browser.get('http://www.baidu.com/')
```

```
3.配置封装：
          from selenium import webdriver
          #这个是浏览器自带的  不需要我们再做额外的操作
          from selenium.webdriver.chrome.options import Options

          def share_browser():
              #初始化
              chrome_options = Options()
              chrome_options.add_argument('--headless')
              chrome_options.add_argument('--disable-gpu')
              #浏览器的安装路径    打开文件位置
              #这个路径是你谷歌浏览器的路径
              path = r'C:\Program Files (x86)\Google\Chrome\Application\chrome.exe'
              chrome_options.binary_location = path

              browser = webdriver.Chrome(chrome_options=chrome_options)

              return  browser
  封装调用：
          from handless import share_browser

          browser = share_browser()

          browser.get('http://www.baidu.com/')

          browser.save_screenshot('handless1.png')
```

### requests

```
1.文档：
	官方文档
		http://cn.python-requests.org/zh_CN/latest/
	快速上手
		http://cn.python-requests.org/zh_CN/latest/user/quickstart.html
```

```
2.安装
	pip install requests
```

```
3.get请求
	requests.get()
		eg:
			 import requests
              url = 'http://www.baidu.com/s?'
              headers = {
                  'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, 				   like Gecko) Chrome/65.0.3325.181 Safari/537.36'
              }
              data = {
                  'wd':'北京'
              }
              response = requests.get(url,params=data,headers=headers)
	定制参数
		参数使用params传递
		参数无需urlencode
	r.text : 获取网站源码
	r.encoding 访问或定制编码方式
	r.url 获取请求的url
	r.content 响应的字节类型
	r.status_code 响应的状态码
	r.headers 响应的头信息
```

```
4:post请求
	requests.post()
	百度翻译:
		eg:
			import requests
			post_url = 'http://fanyi.baidu.com/sug'
             headers={
                  'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 					(KHTML, like Gecko) Chrome/68.0.3440.106 Safari/537.36'
              }
            data = {
                'kw': 'eye'
            }
			r = requests.post(url = post_url,headers=headers,data=data
```

```
5：get和post区别？
	1：get请求的参数名字是params  post请求的参数的名字是data  
	2 请求资源路径后面可以不加?  
	3 不需要手动编解码  4 不需要做请求对象的定制
```

```
6：proxy定制
	在请求中设置proxies参数
	参数类型是一个字典类型
	eg:
		import requests
		url = 'http://www.baidu.com/s?'
         headers = {
              'user-agent': 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, 			  like Gecko) Chrome/65.0.3325.181 Safari/537.36'
          }
        data = {
            'wd':'ip'
        }
        proxy = {
              'http':'219.149.59.250:9797'
          }
	   r = requests.get(url=url,params=data,headers=headers,proxies=proxy)
        with open('proxy.html','w',encoding='utf-8') as fp:
            fp.write(r.text)
```

```
7:cookie定制
	应用案例：
            （1）笑话集
            		http://www.jokeji.cn/
            		账号密码	action   action123
            （2）全书网登陆
            		账号密码    action    action
            （3）chinaunix
            （4）古诗文网（需要验证）
            （5）云打码平台
            	用户登陆   actionuser  action
			   开发者登陆  actioncode  action
```

```
8:cookie定制
header附带cookie
	应用案例：
            （1）笑话集
            		http://www.jokeji.cn/
            		账号密码	action   action123
            （2）全书网登陆
            		账号密码    action    action
            （3）古诗文网（需要验证）
            （4）云打码平台
            	用户登陆   actionuser  action
			   开发者登陆  actioncode  action
```



## scrapy框架

```
1.scrapy是什么？
		Scrapy是一个为了爬取网站数据，提取结构性数据而编写的应用框架。 可以应用在包括数据挖掘，信息处理或存储历史数据等一系列的程序中。
```

```
2.安装scrapy：
			pip install scrapy
  安装过程中出错：
  			如果安装有错误！！！！
             pip install Scrapy
             building 'twisted.test.raiser' extension
             error: Microsoft Visual C++ 14.0 is required. Get it with "Microsoft Visual C++ 			 Build Tools": http://landinghub.visualstudio.com/visual-cpp-build-tools
  解决方案：
		http://www.lfd.uci.edu/~gohlke/pythonlibs/#twisted 
		下载twisted对应版本的whl文件（如我的Twisted-17.5.0-cp36-cp36m-win_amd64.whl），cp后面是            python版本，amd64代表64位，运行命令：
		pip install C:\Users\...\Twisted-17.5.0-cp36-cp36m-win_amd64.whl
		pip install Scrapy
  如果再报错   win32
  解决方法：
  		pip install pypiwin32
  再报错：使用anaconda
```

### scrapy项目的创建以及运行

```
1.创建scrapy项目：
			  终端输入   scrapy startproject  项目名称
```

```
2.项目组成：
          spiders 
              __init__.py
              自定义的爬虫文件.py       ---》由我们自己创建，是实现爬虫核心功能的文件
          __init__.py                  
          items.py                     ---》定义数据结构的地方，是一个继承自scrapy.Item的类
          middlewares.py               ---》中间件   代理
          pipelines.py				  ---》管道文件，里面只有一个类，用于处理下载数据的后续处理
										默认是300优先级，越小优先级越高（1-1000）
          settings.py				  ---》配置文件  比如：是否遵守robots协议，User-Agent定义等
```

```
3.创建爬虫文件：
			（1）跳转到spiders文件夹   cd 目录名字/目录名字/spiders
			（2）scrapy genspider 爬虫名字 网页的域名
  爬虫文件的基本组成：
  			 继承scrapy.Spider类
                                name = 'qiubai'       ---》  运行爬虫文件时使用的名字
                                allowed_domains       ---》 爬虫允许的域名，在爬取的时候，如果不是此域名之下的url，会被过滤掉
                                start_urls			 ---》 声明了爬虫的起始地址，可以写多个url，一般是一个
                                parse(self, response) ---》解析数据的回调函数
                                        response.text
                                        response.body ---》响应的是二进制文件
                                        response.xpath()
                                extract()             ---》提取的是selector对象的是data
                                extract_first()       ---》提取的是selector列表中的第一个数据
```

```
4.运行爬虫文件：
			scrapy crawl 爬虫名称
			注意：应在spiders文件夹内执行
```

扩展：导出文件

```
-o name.json
-o name.xml
-o name.csv
```

### scrapy架构组成

```
        （1）引擎           		---》自动运行，无需关注，会自动组织所有的请求对象，分发给下载器
        （2）下载器				   ---》从引擎处获取到请求对象后，请求数据
        （3）spiders				 ---》Spider类定义了如何爬取某个(或某些)网站。包括了爬取的动作(例如:是否跟进链接)以及如何从网页的内容中提取结构化数据(爬取item)。 换句话说，Spider就是您定义爬取的动作及分析某个网页(或者是有些网页)的地方。
        （4）调度器				   ---》有自己的调度规则，无需关注
        （5）管道（Item pipeline）   ---》最终处理数据的管道，会预留接口供我们处理数据
当Item在Spider中被收集之后，它将会被传递到Item Pipeline，一些组件会按照一定的顺序执行对Item的处理。
每个item pipeline组件(有时称之为“Item Pipeline”)是实现了简单方法的Python类。他们接收到Item并通过它执行一些行为，同时也决定此Item是否继续通过pipeline，或是被丢弃而不再进行处理。
          以下是item pipeline的一些典型应用：
          1. 清理HTML数据
          2. 验证爬取的数据(检查item包含某些字段)
          3. 查重(并丢弃)
          4. 将爬取结果保存到数据库中
```

### scrapy工作原理

![scrapy原理](D:\markdown\data\scrapy原理.png)

### scrapy shell

```
1.什么是scrapy shell？
	Scrapy终端，是一个交互终端，供您在未启动spider的情况下尝试及调试您的爬取代码。 其本意是用来测试提取数据的代码，不过您可以将其作为正常的Python终端，在上面测试任何的Python代码。
该终端是用来测试XPath或CSS表达式，查看他们的工作方式及从爬取的网页中提取的数据。 在编写您的spider时，该终端提供了交互性测试您的表达式代码的功能，免去了每次修改后运行spider的麻烦。
一旦熟悉了Scrapy终端后，您会发现其在开发和调试spider时发挥的巨大作用。
```

```
2.安装ipython
	安装：pip install ipython
	简介：如果您安装了 IPython ，Scrapy终端将使用 IPython (替代标准Python终端)。 IPython 终端与其他相比更为强大，提供智能的自动补全，高亮输出，及其他特性。
```

```
3.应用：（1）scrapy shell www.baidu.com
       （2）scrapy shell http://www.baidu.com
        (3) scrapy shell "http://www.baidu.com"
        (4) scrapy shell "www.baidu.com"

语法：
	（1）response对象：
                  response.body
                  response.text
                  response.url
                  response.status
    （2）response的解析：
                  response.xpath()
                  			 使用xpath路径查询特定元素，返回一个selector列表对象
                  response.css()
                  			 使用css_selector查询元素，返回一个selector列表对象
                              获取内容 ：response.css('#su::text').extract_first()
                              获取属性 ：response.css('#su::attr(“value”)').extract_first()
    （3）selector对象（通过xpath方法调用返回的是seletor列表）
                  extract()
                  			 使用xpath请求到的对象是一个selector对象，需要进一步使用extract()方法拆包，转换为unicode字符串
                  extract_first()
                  			 返回第一个解析到的值，如果列表为空，此种方法也不会报错，会返回一个空值
                  xpath()
                  css()
                  			 注意：每一个selector对象可以再次的去使用xpath或者css方法

    （4）item对象
                  dict(itemobj)
                  			 可以使用dict方法直接将item对象转换成字典对象
                  Item(dicobj)
                  			 可以使用字典对象创建一个Item对象
```

### yield

```
1. 带有 yield 的函数不再是一个普通函数，而是一个生成器generator，可用于迭代
2. yield 是一个类似 return 的关键字，迭代一次遇到yield时就返回yield后面(右边)的值。重点是：下一次迭代时，从上一次迭代遇到的yield后面的代码(下一行)开始执行
3. 简要理解：yield就是 return 返回一个值，并且记住这个返回的位置，下次迭代就从这个位置后(下一行)开始

name_list = [x for x in range(10)]
def createGenorator():
	items = []
	for i in name_list:
		print('第{}次调用'.format(i))
		items.append(i)
	return items
def testFunc1():
	generator = createGenorator2()
	for a in generator:
		print('使用第{}次'.format(a))

def createGenorator2():
	for i in name_list:
		print('第{}次调用'.format(i))
		yield i
print(testFunc1())
```

### pymysql的使用步骤（sqlalchemy）

```
1.pip install pymysql
2.pymysql.connect(host,port,user,password,db,charset)
3.conn.cursor()
4.cursor.execute()

pip install sqlalchemy
import sqlalchemy
conn = sqlalchemy.create_engine('mysql+pymsql://user:password@host:port/database?charset')
charset可以省略
```

### CrawlSpider

```
1.继承自scrapy.Spider
2.独门秘笈
	CrawlSpider可以定义规则，再解析html内容的时候，可以根据链接规则提取出指定的链接，然后再向这些链接发送请求
	所以，如果有需要跟进链接的需求，意思就是爬取了网页之后，需要提取链接再次爬取，使用CrawlSpider是非常合适的
```

```
3.提取链接
	链接提取器，在这里就可以写规则提取指定链接
scrapy.linkextractors.LinkExtractor(
	 allow = (),           # 正则表达式  提取符合正则的链接
	 deny = (),            # (不用)正则表达式  不提取符合正则的链接
	 allow_domains = (),   # （不用）允许的域名
	 deny_domains = (),    # （不用）不允许的域名
	 restrict_xpaths = (), # xpath，提取符合xpath规则的链接
	 restrict_css = ()     # 提取符合选择器规则的链接)
4.模拟使用
		正则用法：links1 = LinkExtractor(allow=r'list_23_\d+\.html')
		xpath用法：links2 = LinkExtractor(restrict_xpaths=r'//div[@class="x"]')
		css用法：links3 = LinkExtractor(restrict_css='.x')
5.提取连接
		link.extract_links(response)
```

```
6.注意事项
	【注1】callback只能写函数名字符串, callback='parse_item'
	【注2】在基本的spider中，如果重新发送请求，那里的callback写的是   callback=self.parse_item 【注--稍后看】follow=true 是否跟进 就是按照提取连接规则进行提取
```

### CrawlSpider案例

```
1.创建项目：scrapy startproject dushuproject
2.跳转到spiders路径  cd\dushuproject\dushuproject\spiders
3.创建爬虫类：scrapy genspider -t crawl read www.dushu.com
4.items
5.spiders
6.settings
7.pipelines
		数据保存到本地
		数据保存到mysql数据库
```

### 数据入库

```
（1）settings配置参数：
			 DB_HOST = '192.168.231.128'
              DB_PORT = 3306
              DB_USER = 'root'
              DB_PASSWORD = '1234'
              DB_NAME = 'test'
              DB_CHARSET = 'utf8'
（2）管道配置
              from scrapy.utils.project import get_project_settings
              import pymysql
              class MysqlPipeline(object):
                  """docstring for MysqlPipeline"""
                  def __init__(self):
                      settings = get_project_settings()
                      self.host = settings['DB_HOST']
                      self.port = settings['DB_PORT']
                      self.user = settings['DB_USER']
                      self.pwd = settings['DB_PWD']
                      self.name = settings['DB_NAME']
                      self.charset = settings['DB_CHARSET']

                      self.connect()

                 def connect(self):
                      self.conn = pymysql.connect(host=self.host,
                                                 port=self.port,
                                                 user=self.user,
                                                 password=self.pwd,
                                                 db=self.name,
                                                 charset=self.charset)
                      self.cursor = self.conn.cursor()

                def close_spider(self, spider):
                    self.conn.close()
                    self.cursor.close()

                def process_item(self, item, spider):
                    sql = 'insert into book(image_url, book_name, author, info) values("%s", "%s", "%s", "%s")' % (item['image_url'], item['book_name'], item['author'], item['info'])
                    
                    sql = 'insert into book(image_url,book_name,author,info) values
 ("{}","{}","{}","{}")'.format(item['image_url'], item['book_name'], item['author'], item['info'])
                    # 执行sql语句
                    self.cursor.execute(sql)
                    self.conn.commit()
                    return item
```

### 日志信息和日志等级

```
（1）日志级别：
            CRITICAL：严重错误
            ERROR：一般错误
            WARNING：警告
            INFO: 一般信息
            DEBUG：调试信息
            
            默认的日志等级是DEBUG
            只要出现了DEBUG或者DEBUG以上等级的日志
            那么这些日志将会打印
（2）settings.py文件设置：
		   默认的级别为DEBUG，会显示上面所有的信息
            在配置文件中  settings.py
            LOG_FILE  : （文件名）将屏幕显示的信息全部记录到文件中，屏幕不再显示，注意文件后缀一定是.log
            LOG_LEVEL : （上面的日志级别）设置日志显示的等级，就是显示哪些，不显示哪些
```

### Request和response总结

```
Request 是一个类
	get请求
		scrapy.Request(url=url, callback=self.parse_item, meta={'item': item}, headers=headers)
                url: 要请求的地址
                callback：响应成功之后的回调函数
                meta: 参数传递  接收的语法：item = response.meta['item']
                headers: 定制头信息，一般不用      parse_item方法中的response参数就是url执行之后的请求结果
```

```
response 是一个对象 函数的第二个参数
               	response.text: 字符串格式的文本
                response.body: 二进制格式的文本
                response.url: 当前响应的url地址
                response.status: 状态码
                response.xpath(): 筛选你想要的内容
                response.css(): 筛选你想要的内容
```

### scrapy的post请求

```
（1）重写start_requests方法：
		def start_requests(self)
 (2) start_requests的返回值：
 	 scrapy.FormRequest(url=url, headers=headers, callback=self.parse_item, formdata=data)
            url: 要发送的post地址
            headers：可以定制头信息
            callback: 回调函数   
            formdata: post所携带的数据，这是一个字典
```

### 代理（通过下载中间件来进行添加）

```
	（1）到settings.py中，打开一个选项
		DOWNLOADER_MIDDLEWARES = {
		   'postproject.middlewares.Proxy': 543,
		}
	（2）到middlewares.py中写代码
		def process_request(self, request, spider):
	        request.meta['proxy'] = 'https://113.68.202.10:9999'
	        return None
```

### cookie登陆

```
案例：微博网登陆
代码：
import scrapy
class WbSpider(scrapy.Spider):
    name = 'wb'
    allowed_domains = ['weibo.cn']
    
    def start_requests(self):
        url = 'https://passport.weibo.cn/sso/login'
        headers={
            'accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3',
            # 'accept-encoding': 'gzip, deflate, br',
            'accept-language': 'zh-CN,zh;q=0.9',
            'cache-control': 'max-age=0',
            'cookie': 'SCF=Ahi2Sm3XHpcYIJvIsbJd8AnqkyO8t5RFmHXn8yHeTOMYgumvEqFGsgNbZbD6BmzlV7GA-B8sNWcbTcHeVmF3eNc.; _T_WM=32e4d519b787dd16fa96e2224b27a576; SUB=_2A25x8xaODeRhGeBK7lMV-S_JwzqIHXVTH7rGrDV6PUJbkdAKLVHlkW1NR6e0UBazrACpD1Cukh54U8WxKn23yIXs; SUHB=08JLxm5YJpiTJ1; SSOLoginState=1559717598',
            'referer': 'https://weibo.cn/',
            'upgrade-insecure-requests': '1',
            'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36',
        }
        data = {
            'username': '18642820892',
            'password': 'lijing1150501',
            'savestate': '1',
            'r': 'https://weibo.cn/',
            'ec': '0',
            'pagerefer': 'https://weibo.cn/pub/',
            'entry': 'mweibo',
            'wentry': '',
            'loginfrom': '',
            'client_id': '',
            'code': '',
            'qq': '',
            'mainpageflag': '1',
            'hff': '',
            'hfp': '',
        }
        yield scrapy.FormRequest(url=url,callback=self.parse_item,formdata=data,headers=headers)

    def parse_item(self,response):
        url = 'https://weibo.cn/6451491586/info'
        headers = {
            'accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3',
            # 'accept-encoding': 'gzip, deflate, br',
            'accept-language': 'zh-CN,zh;q=0.9',
            'cache-control': 'max-age=0',
            'cookie': 'SCF=Ahi2Sm3XHpcYIJvIsbJd8AnqkyO8t5RFmHXn8yHeTOMYgumvEqFGsgNbZbD6BmzlV7GA-B8sNWcbTcHeVmF3eNc.; _T_WM=32e4d519b787dd16fa96e2224b27a576; SUB=_2A25x8xllDeRhGeBK7lMV-S_JwzqIHXVTH6ctrDV6PUJbkdAKLRjYkW1NR6e0UHabYnrx2IRT40S735NJ0JgW9T6S; SUHB=0LciE0Eb6CLyKh; SSOLoginState=1559718197',
            'referer': 'https://weibo.cn/',
            'upgrade-insecure-requests': '1',
            'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36',
        }
        yield scrapy.Request(url=url,callback=self.parse_item1,headers=headers)

    def parse_item1(self,response):
        content = response.text
        with open('weibo.html','w',encoding='utf-8')as fp:
            fp.write(content)
```

### 分布式爬虫准备工作

1.linux下Python环境搭建、scrapy安装。

```
pip3 install scrapy
pip3 install scrapy_redis
```

2.redis安装

```
windows
	（1）下载msi安装包，安装过程需要将添加环境变量、过滤防火墙选中，内存使用默认100M即可
	（2）启动：
              cd C:\Program Files\Redis
                  跳转到redis的安装目录下
              redis-server.exe redis.windows.conf
                  启动redis服务
              redis-cli
          发生启动错误信息
              creating server tcp listening socket 127.0.0.1:6379: bind No error
          解决办法
                  1. redis-cli.exe
                  2. shutdown
                  3. exit
                  4. redis-server.exe redis.windows.conf
	（3）本地连接
		redis-cli
	（4）远程连接限制
		windows上面的redis配置文件中有限制，只允许本机连接，所以我们需要来修改一下配置，让远程linux连接
		来到redis的安装路径   C:\Program Files\Redis
		redis的配置文件就是   redis.windows.conf
		修改配置文件
              第56行   注释掉这一行   前面添加#号
              第75行   protected-mode no
	（5）远程连接
				指令：(默认端口号都是6379，可以不加)
                  redis-cli -h host -p port      
                  redis-cli -h 10.11.63.79
注：linux安装见tornado—redis文档
```

1. 扩展：1.redis数据类型（http://www.runoob.com/redis/redis-sorted-sets.html）

   ​	    2.redis常见问题（https://blog.csdn.net/hjm4702192/article/details/80518856）

2. 分布式安装

   windows：pip install scrapy_redis

   linux：       pip3 install scrapy_redis

### scrapy和scrapy_redis区别？

```
（1）scrapy是一个通用的爬虫框架，但是这个框架不支持分布式
（2）scrapy_redis就是为了实现scrapy的分布式而诞生的，它提供了一些基于redis的组件
	（https://www.cnblogs.com/nick477931661/p/9135497.html）
```

### scrapy_redis官方案例介绍

（https://github.com/rmax/scrapy-redis）

```
1.声明普通的spider类继承的是scrapy.spider
2.dmoz 普通的crawlspider类
                        连接提取的spider
3.myspider_redis 继承的是RedisSpider
            （1）普通的spider的分布式
            （2）  def __init__(self, *args, **kwargs):
                         # Dynamically define the allowed domains list.
                         domain = kwargs.pop('domain', '')
                         self.allowed_domains = filter(None, domain.split(','))
                         super(MySpider, self).__init__(*args, **kwargs)
                         官方文档指定的init的暂时不可以代替allowed_domains
                         所以我们还是要使用allowd_domains
             (3)指定redis_key
                eg:redis_key = 'mycrawler:start_urls'
4.mycrawler_redis 继承的是RedisCrawlSpider
             (1)连接提取的分布式
             (2)def __init__(self, *args, **kwargs):
                      # Dynamically define the allowed domains list.
                      domain = kwargs.pop('domain', '')
                      self.allowed_domains = filter(None, domain.split(','))
                      super(MySpider, self).__init__(*args, **kwargs)
                      官方文档指定的init的暂时不可以代替allowed_domains
                      所以我们还是要使用allowd_domains
              (3)指定redis_key
                 eg:redis_key = 'mycrawler:start_urls'
5.新增组件
from scrapy_redis.spiders import RedisSpider
from scrapy_redis.spiders import RedisCrawlSpider
这两个就是scrapy_redis新增加的两个组件，都是继承自官方的Spider、CrawlSpider
```

```
DOWNLOAD_DELAY = 1
【注】在爬取网站的时候，将这个选项打开，给对方一条活路
```

### 多台电脑部署分布式

```
现在有4台电脑：windows   centos  ubuntu   macos
windows上面安装的是redis服务器，master端
	centos、ubuntu、macos都从redis上面获取请求，或者将请求添加到redis服务器中，   slave端
	slave端首先启动，页面就会停止在那里等待指令
	这个时候master通过lpush向队列中添加一个起始url，其中一个slave端获取到这个url开始爬取，这个slave端会将解析之后的很多url再次的添加到redis服务中，然后redis服务再从请求队列中向每个slave端分发请求，最终直到所有请求爬取完毕为止
```

```
分布式settings基本配置：
             （1）使用的是scrapy_redis的去重类
              	  DUPEFILTER_CLASS = "scrapy_redis.dupefilter.RFPDupeFilter"
             （2）调度器使用是scrapy_redis的调度器
              	  SCHEDULER = "scrapy_redis.scheduler.Scheduler"
             （3）爬取的过程中是否允许暂停
                  SCHEDULER_PERSIST = True
             （4）配置存储的redis服务器
                  REDIS_HOST = '10.11.52.62'
                  REDIS_PORT = 6379
                  ITEM_PIPELINES = {
                     'scrapy_redis.pipelines.RedisPipeline': 400,
                  }
```

```
scrapy-redis执行代码：
	（1）slave端执行scrapy runspider mycrawler_redis.py
	（2）master端向队列中添加起始url
		这个key就是你代码中写的  redis_key
		lpush fen:start_urls 'http://www.dytt8.net/html/gndy/dyzz/index.html'
```

### 分布式爬虫原理



```
如何去重？
这里借助redis的集合，redis提供集合数据结构，在redis集合中存储每个request的指纹
在向request队列中加入Request前先验证这个Request的指纹是否已经加入集合中。如果已经存在则不添加到request队列中，如果不存在，则将request加入到队列并将指纹加入集合

如何防止中断？如果某个slave因为特殊原因宕机，如何解决？
这里是做了启动判断，在每台slave的Scrapy启动的时候都会判断当前redis request队列是否为空
如果不为空，则从队列中获取下一个request执行爬取。如果为空则重新开始爬取，第一台丛集执行爬取向队列中添加request
```

作业：1.预习分布式爬虫

​            2.房天下   全国所有的二手房，和新房的房源 ​

### 房天下数据下载

```
实现目标：
		(1).爬取全国所有城市的新房
         (2).爬取全国所有城市的二手房
实现效果：
{
  "province": "辽宁",
  "city": "大连",
  "name": " 通州均价三万,花园洋房,现房精装近地铁,独立大房本",
  "price": "234万"
}{
  "province": "直辖市",
  "city": "北京",
  "name": " 孔雀城原山著北欧联排,观景佳,依山建,透明价",
  "price": "280万"
}
```

案例：国家统计局（http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2017/）共计68万条数

#### 2.进程

```
进程：直观点说，保存在硬盘上的程序运行以后，会在内存空间里形成一个独立的内存体，这个内存体有自己独立的地址空间，有自己的堆，上级挂靠单位是操作系统。操作系统会以进程为单位，分配系统资源（CPU时间片、内存等资源），进程是资源分配的最小单位、
```

```
系统由一个个进程(程序)组成,一般情况下，包括文本区域（text region）、数据区域（data region）和堆栈（stack region）。
（1）文本区域存储处理器执行的代码
（2）数据区域存储变量和进程执行期间使用的动态分配的内存；
（3）堆栈区域存储着活动过程调用的指令和本地变量。
因此进程的创建和销毁都是相对于系统资源,所以是一种比较昂贵的操作。 
进程有三个状态:
              等待态：等待某个事件的完成；
              就绪态：等待系统分配处理器以便运行；
              运行态：占有处理器正在运行。
进程是抢占式的争夺CPU运行自身,而CPU单核的情况下同一时间只能执行一个进程的代码,但是多进程的实现则是通过CPU飞快的切换不同进程,因此使得看上去就像是多个进程在同时进行.
```

#### 3.线程

```
线程，有时被称为轻量级进程(Lightweight Process，LWP），是操作系统调度（CPU调度）执行的最小单位。
（1）线程属于进程
（2）线程共享进程的内存地址空间
（3）线程几乎不占有系统资源
通信问题:   进程相当于一个容器,而线程而是运行在容器里面的,因此对于容器内的东西,线程是共同享有的,因此线程间的通信可以直接通过全局变量进行通信,但是由此带来的例如多个线程读写同一个地址变量的时候则将带来不可预期的后果,因此这时候引入了各种锁的作用,例如互斥锁等。
```

![线程](C:\Users\lijingAction\Desktop\SH-1905-爬虫\day09\doc\线程.jpg)

```
（1）进程是系统分配资源的最小单位
（2）线程是CPU调度的最小单位
（3）由于默认进程内只有一个线程,所以多核CPU处理多进程就像是一个进程一个核心
```

```
线程和进程的上下文切换步骤：
                进程切换分3步:
                （1）切换页目录以使用新的地址空间
                （2）切换内核栈
                （3）切换硬件上下文
                    而线程切换只需要第2、3步,因此进程的切换代价比较大
```

#### 4.协程

```
（1）协程是属于线程的。协程程序是在线程里面跑的，因此协程又称微线程和纤程等
（2）协程没有线程的上下文切换消耗。协程的调度切换是用户(程序员)手动切换的,因此更加灵活,因此又叫用户空间线程.
（3）原子操作性。由于协程是用户调度的，所以不会出现执行一半的代码片段被强制中断了，因此无需原子操作锁。
```

协程的实现

```
协程的实现：迭代器和生成器
            迭代器： 实现了迭代接口的类,接口函数例如:current,key,next,rewind,valid。迭代器最基本的规定了对象可以通过next返回下一个值，而不是像数组，列表一样一次性返回。语言实现：在Java的foreach遍历迭代器对(数组)，Python的for遍历迭代器对象(tuple，list，dict)。
            生成器： 使用 yield 关键字的函数,可以多次返回值，生成器实际上也算是实现了迭代器接口(协议)。即生成器也可通过next返回下一个值。
```

```
协程举例：在Python中，使用了yield的函数为生成器函数，即可以多次返回值。则生成器可以暂停一下，转而执行其他代码，再回来继续执行函数往下的代码
```

#### 5.总结：进程、线程对比

```
功能对比：
        进程，能够完成多任务，比如 在一台电脑上能够同时运行多个QQ
        线程，能够完成多任务，比如 一个QQ中的多个聊天窗口
```

```
定义的不同：
        进程:系统进行资源分配和调度的一个独立单位.
        线程:进程的一个实体,是CPU调度和分派的基本单位,它是比进程更小的能独立运行的基本单位.线程自己基本上不拥有系统资源,只拥有一点在运行中必不可少的资源(如程序计数器,一组寄存器和栈),但是它可与同属一个进程的其他的线程共享进程所拥有的全部资源.
```

```
区别:
        (1)一个程序至少有一个进程,一个进程至少有一个线程.
        (2)线程的划分尺度小于进程(资源比进程少)，使得多线程程序的并发性高。
        (3)进程在执行过程中拥有独立的内存单元，而多个线程共享内存，从而极大地提高了程序的运行效率 
        (4)线程不能够独立执行，必须依存在进程中
        (5)可以将进程理解为工厂中的一条流水线，而其中的线程就是这个流水线上的工人 
```

```
优缺点:
        线程和进程在使用上各有优缺点：线程执行开销小，但不利于资源的管理和保护；而进程正相反。
```

#### 6.总结：进程、线程、协程对比

```
简答案例：
        有一个老板想要开个工厂进行生产某件商品（例如剪子）
        他需要花一些财力物力制作一条生产线，这个生产线上有很多的器件以及材料这些所有的 为了能够生产剪子而准备的资源称之为：进程
        只有生产线是不能够进行生产的，所以老板的找个工人来进行生产，这个工人能够利用这些材料最终一步步的将剪子做出来，这个来做事情的工人称之为：线程
        这个老板为了提高生产率，想到3种办法：
        （1）在这条生产线上多招些工人，一起来做剪子，这样效率是成倍増长，即单进程 多线程方式
        （2）老板发现这条生产线上的工人不是越多越好，因为一条生产线的资源以及材料毕竟有限，所以老板又花了些财力物力购置了另外一条生产线，然后再招些工人这样效率又再一步提高了，即多进程 多线程方式
        （3）老板发现，现在已经有了很多条生产线，并且每条生产线上已经有很多工人了（即程序是多进程的，每个进程中又有多个线程），为了再次提高效率，老板想了个损招，规定：如果某个员工在上班时临时没事或者再等待某些条件（比如等待另一个工人生产完谋道工序 之后他才能再次工作） ，那么这个员工就利用这个时间去做其它的事情，那么也就是说：如果一个线程等待某些条件，可以充分利用这个时间去做其它事情，其实这就是：协程方式
```

```
简单总结：
        （1）进程是资源分配的单位
        （2）线程是操作系统调度的单位
        （3）进程切换需要的资源很最大，效率很低
        （4）线程切换需要的资源一般，效率一般（当然了在不考虑GIL的情况下）
        （5）协程切换任务资源很小，效率高
        （6）多进程、多线程根据cpu核数不一样可能是并行的，但是协程是在一个线程中 所以是并发
```

案例：多线程爬取糗事百科
