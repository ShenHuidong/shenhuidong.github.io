---
layout: default
title: 你好，世界
---
###登录接口

##1.登录接口
{% highlight ruby %}
def foo
  puts 'foo'
end
{% endhighlight %}


{% gist 5555251 %}



Api路径：Login/login

请求方式：post

参数：

|参数 | 描述 |必选|取值范围|
| -------- | -------- |-------- |--------|
|phone    |手机号    |是    |String|
|password    |密码    |是    |String|

返回值：

| 参数 | 描述 |取值范围
| -------- | -------- |--------
|code    |返回编码        |  1 登录成功，返回token <br />-1 登录失败，密码错误<br />-2 登录失败，账户不存在<br />-3 登录失败，账户被禁用<br />-4 登录失败，token写入数据库失败<br />-5 参数不合法
|data|数据|登录成功后返回token数据|       
|message    |消息提示       |发生错误时，直接显示接口的报错信息
|addtion_data    |额外信息    |混编

返回值示例：
```
{
    "code": 1,
    "data": {
        "workerId": "3",
        "token": "eae93323df2fcb3799757f5ed9573f4f",
        "refreshToken": "7a5b1384de62ac43227b462f20e1c75a",
        "tokenExpire": "2017-02-10 10:37:52",
        "refreshTokenExpire": "2016-03-17 10:37:52"
    },
    "message": "登录成功",
    "addtion_data": ""
}
{
    "code": -1,
    "data": "",
    "message": "密码错误",
    "addtion_data": ""
}
{
    "code": -2,
    "data": "",
    "message": "账户不存在",
    "addtion_data": ""
}
{
    "code": -5,
    "data": "",
    "message": "参数不正确",
    "addtion_data": ""
}
```

##2.安全退出接口

Api路径：Login/logout

请求方式：post

参数：

|参数 | 描述 |必选|取值范围|
| -------- | -------- |-------- |--------|
|token|token    |是    |String|


返回值：

| 参数 | 描述 |取值范围
| -------- | -------- |--------
|code    |返回编码        |  1 已安全退出 <br />-1 请求中不包含token<br />-2 参数token不合法！<br />-3 退出失败,提供的vendorId有误！<br />-4 登录失败，token写入数据库失败
|data|数据|空|       
|message    |消息提示       |发生错误时，直接显示接口的报错信息
|addtion_data    |额外信息    |混编

返回值示例：
```
{
    "code": 1,
    "data": "",
    "message": "已安全退出！",
    "addtion_data": ""
}

{
    "code": -1,
    "data": "",
    "message": "请求中不包含token",
    "addtion_data": ""
}

{
    "code": -2,
    "data": "",
    "message": "参数token不合法！",
    "addtion_data": ""
}


{
    "code": -3,
    "data": "",
    "message": "退出失败,提供的vendorId有误！",
    "addtion_data": ""
}

```