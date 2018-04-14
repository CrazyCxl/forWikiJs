<!-- TITLE: 暴力破解 -->
<!-- SUBTITLE: A quick summary of 暴力破解 -->

# crunch
*生成密码字典*
参考：https://null-byte.wonderhowto.com/how-to/hack-like-pro-crack-passwords-part-4-creating-custom-wordlist-with-crunch-0156817/
下载地址：https://sourceforge.net/projects/crunch-wordlist/


# hydra
## 安装
### fedora
>dnf install hydra

## 网页登录破解
参考：https://null-byte.wonderhowto.com/how-to/hack-like-pro-crack-online-web-form-passwords-with-thc-hydra-burp-suite-0160643/
帮助：
>hydra -U http-post-form

**注意：该方式访问json数据时可能会有问题，试过几个方法皆未成功** [^json_error]

curl post 访问测试连接
>curl -l -H "Content-type: application/json" -X POST -d '{"phone":"13521389587","password":"test"}' http://domain/apis/login

[^json_error]:(https://security.stackexchange.com/questions/57839/hydra-bruteforce-and-json/57858)

