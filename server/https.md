# HTTPS

## What is HTTPS?

`HTTPS` stands for `Hyper Text Transfer Protocol Secure`. It is a protocol for securing the comunication between 2 system (e.g. the browser and the web server).
`HTTPS` established an encrypted link between the browser and the web server using one of the 2 protocols below:

- `SSL`:Secure Socket Layer, `SSL` establishes an encryed link using an SSL certificate which is also known as a digital certificate.
- `TLS`: Transport Layer Security(new version of SSL)

## HTTP VS HTTPS

|HTTP|HTTPS|
|-|-|
|Transfers data in hypertext format|Transfers data in encryed format|
|Uses port 80 by default|Uses port 443 by default|
|Not secure|Secured using SSL technology|
|starts with http:// | starts with https:// |

## How to Get an SSL Certificate

You can get an SSL cetificate from any authorized CA(Certificate Authority).There are two ways to get an SSL certificate.

- Buy a certificate from CA from
  - Comodo
  - Digicert
  - RapidSSL
  - GeoTrust
  - theSSLStore.com
- Get a free certificate from a non-profit open CA
  - https://letsencrypt.org/

## Steps

- Generate a CSR (Certificate Signing Request) from your web server
- Submit it to the CA
- the CA will take some time for validating your info.
- Download the SSL certificate after successful validation
- Install an SSL certification on your web server.

## certbot

- choose nginx on ubuntu 18.04
- ssh root@xxx.xx.xx.xx
跟着一步一步操作即可。傻瓜式

## 参考
- [https://github.com/Neilpang/acme.sh](https://github.com/Neilpang/acme.sh)
- [https://arashmilani.com/post?id=95](https://arashmilani.com/post?id=95)

