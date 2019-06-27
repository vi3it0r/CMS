# Niushop B2B2C 多商户基础版V1.11中管理员任意密码重置

说明：NiuShop开源商城系统是一套PHP开源电子商务系统。Niushop B2B2C 多商户基础版V1.11中身份验证可以绕过从而造成管理员任意密码重置。

## 1.技术说明

位于\application\shop\controller\Login.php 行：757~!769

![img](1.png)
此处验证码采用php “==”验证，可用php弱类型绕过

## 2.poc
正常提交会显示验证码不一致
![img](2.png)

用burpsuit抓包，在send_parem后加上数组，即可绕过php弱类型同时不为空。
![img](3.png)
因为验证码已经认定身份，将管理员手机号提交为空即可重置密码
![img](5.png)
登录成功
![img](6.png)