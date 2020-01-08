# How to use openssl sign and verify file

1 generate PEM format ECC parameter to file

```shell
openssl genpkey -genparam -algorithm ec -pkeyopt ec_paramgen_curve:secp256k1 -out secp256k1.param
```

2 generate private key from PEM format parameter file.

```sh
openssl genpkey -paramfile secp256k1.param -out my.key
```

3 Check out key file

```sh
openssl pkey -in my.key -text -noout
```

4 generate signed file

```sh
openssl dgst -sign my.key -sha512 -out signature-file file-to-be-signed 
```

5 generate public key from private key

```sh
openssl ec -in my.key -pubout -out pub.pem
```

6 verify signing

```sh
openssl dgst -verify pub.pem -sha512 -signature signature-file file-to-be-signed
```





# Reference

1 椭圆曲线密码学相关概念与开源实现.

https://www.8btc.com/article/128018

2 Command Line Elliptic Curve Operations.

https://wiki.openssl.org/index.php/Command_Line_Elliptic_Curve_Operations:w

