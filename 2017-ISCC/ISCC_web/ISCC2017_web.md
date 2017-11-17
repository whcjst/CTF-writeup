web题复现难度比较高，所以没有源码的题目只能各自YY了。


### 0x01 Web签到题，来和我换flag啊！

POST提交hiddenflag=f1ag&flag=f1ag&FLAG=f1ag 得到flag

![](http://oohnuejim.bkt.clouddn.com/Image.png)



----------

### 0x02 WelcomeToMySQL



源码
hint:$servername,$username,$password,$db,$tb is set in ../base.php
上传pht，连上菜刀，查看目录底下的base.php为数据库密码
连上数据库，查看flag的字段。
![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/f71687f9-d3f8-4a63-802f-2448530d01e9.png)



![](http://oohnuejim.bkt.clouddn.com/Image.png)

----------
### 0x03 where is your flag

首先是猜get参数，访问/?id=1，返回了******flag is in flag。访问/?id=2，页面返回空白，说明这个get参数是有用的。访问/?id=1%df%27出现了报错，说明存在宽字节注入

![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/1e74680a-d6bf-416b-ba08-d6b4664c5125.png)
最后用注入工具盲注出flag
![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/9c889724-f428-4fbb-856b-5a6f8a4a8244.png)



----------
### 00x4 我们一起来日站

扫目录，robots.txt

再扫描/2   那个很长的目录，看见后台。2次post注入

![](http://oohnuejim.bkt.clouddn.com/iscc_web_3.png)
