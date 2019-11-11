# HMAC

HMAC是密钥相关的哈希运算消息认证码（Hash-based Message Authentication Code）的缩写，由H.Krawezyk，M.Bellare，R.Canetti于1996年提出的一种基于Hash函数和密钥进行消息认证的方法，并于1997年作为RFC2104被公布，并在IPSec和SSL中得以广泛应用，它可以与任何迭代散列函数捆绑使用。

HMAC 是用于消息认证的加密哈希算法，**HMAC利用哈希算法，以一个密钥和一个消息作为输入，生成一个加密串作为输出**。HMAC 可以有效防止类似 MD5 的彩虹表等攻击。

# Python 实现

```py
#!/usr/bin/env python

import hashlib
import hmac

#keyword=raw_input("Please input keyword:")
msg = "The quick brown fox jumps over the lazy dog"
key = "key"
m = hmac.new(key, msg, hashlib.sha256)
signature = m.hexdigest()
print(signature)

```

计算结果：

```shell
$ f7bc83f430538424b13298e6aa6fb143ef4d59a14946175997479dbc2d1a3cd8
```

# HMAC在bitcoin 的应用

比特币的钱包使用密钥延伸函数PBKDF2，而PBKDF2使用HMAC-SHA512算法，用2048次哈希来延伸助记符和盐参数，产生一个512位的值作为其最终输出。 这个512位的值就是种子（seed）。



参考文献：

1 hmac. https://en.wikipedia.org/wiki/HMAC

2 hmac. https://baike.baidu.com/item/hmac

3 hmac. https://www.liaoxuefeng.com/wiki/1016959663602400/1183198304823296

4 硬件实现HMAC. https://docs.opentitan.org/hw/ip/hmac/doc/

5 比特币的HD钱包演化-3. 

https://happy123.me/blog/2018/11/07/bi-te-bi-de-hdqian-bao-yan-hua-3/

6 比特币钱包. https://aaron67.cc/2019/01/22/bitcoin-wallet/

