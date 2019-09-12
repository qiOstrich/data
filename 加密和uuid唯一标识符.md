# 加密

为了让密码在网络传输中更加安全，需要对密码进行加密。

## MD5加密

md5加密可以在hashlib模块直接调用

```python
import hashlib
md = hashlib.md5()
md.update(str.encode('utf-8'))
me.digest()#取得加密结果，二进制
me.hexdigest()#取得加密结果，十六进制
```

## sha加密

sha加密有4中不同长度的加密：

1. sha224()
2. sha256()
3. sha384()
4. sha512()

```python
import hashlib
sh = hashlib.sha224()
sh.update(ste.encode('utf-8'))
sh.digest()
sh.hexdigest()
```

四种加密方式的用法相同，不重复书写。

## hmac加密

hmac加密是需要使用密钥的加密方式，更加安全。

```python
import hmac
hm = hmac(key.encode('utf-8'))
hm.update(str.encode('utf-8'))
hm.hexdigest()
hm.digest()
```

## uuid唯一标识符

意义：识别用户的唯一性

```python
uu1=uuid.uuid1()
uu3=uuid.uuid3(uuid.NAMESPACE_URL,str)
uu4=uuid.uuid4()
uu5=uuid.uuid5(uuid.NAMESPACE_URL,str)
```

在python3中已经废弃UUID2

平时建议使用uuid1和uuid3

因为简单！！！