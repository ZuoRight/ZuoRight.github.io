# HTTPS

参考文章：
https://github.com/youngwind/blog/issues/108
https://iswbm.com/72.html

- 单向认证：客户端对服务端做认证
- 双向认证：客户端和服务端互相认证

## 基础知识

客户端
对称加密

服务端
非对称加密
- 服务端私钥
- 服务端公钥

证书中心/根证书：系统自带、手动安装
作用：用根证书公钥解密CA，得到服务端公钥
- 根证书私钥
- 根证书公钥
- 根证书签名：根证书私钥加密得到

## 对称加密

特点：效率高，但安全系数低

算法：AES(最常用)、DES、RC4

## 非对称加密

特点：安全系数高，但效率低

算法：RSA(最常用)、ECC、DH

OpenSSL生成密钥对

私钥加密公钥解密，通常用来生成签名
公钥加密私钥解密，公钥可以验证私钥生成的签名

## 信息摘要

概念：将一段任意长度的信息通过摘要算法转变成一串固定长度的哈希值，不可逆，所以它并不是用于加密信息，而是用于验证信息的完整性

特点：两段不同的信息，可能会被转变成同一串哈希值

算法：MD5、SHA1、SHA256、SHA512

## 数字签名

概念：信息摘要通过私钥加密（签名）便成为了数字签名，可通过公钥解密（验签），用于验证摘要的正确性

## 数字证书

[CSR在线生成工具](https://myssl.com/csr_create.html)

申请者（个人或机构）将CSR(Certificate Signing Request)文件（即证书请求文件，包含公钥、申请者信息、域名等信息）提交给CA(Certificate Authority 证书授权中心，类似公安局)

CA验证通过（组织存在，企业合法，确实是域名的拥有者），使用哈希算法得到信息摘要，用CA的私钥加密生成数字签名

然后将csr文件和数字签名打包成数字证书，返回给申请者，存入服务端

### 证书编码格式

PEM：明文格式
DER：二进制格式

### 证书的扩展名

.csr：一般用于证书签名请求文件
.cer：常用于Windows系统
.crt：常用于类unix系统
.key
.p12

### 证书种类

按安全等级分为：

DV，安全等级低，只验证域名所有权，仅起到数据加密的作用，免费证书一般都是这个
OV，安全等级中，会对申请者身份做验证
EV，安全等级高，全球通用

按保护域名的数量分为：

单域名版：只保护一个域名
多域名版：保护多个域名
通配符版：保护主域名下同一级的所有子域名