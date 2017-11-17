### 0x01 Wheel Cipher

提示是二战时期的密码，然后看观察下题目发现是轮盘密码

![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/08d338d0-d6de-4f89-93f1-6d027326434f.png)


![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/2f202718-f391-4821-b547-8e0cb2785268.png)


脚本

![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/47858d55-36bf-4400-acaf-591a80b5fa15.png)


![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/3bd09d13-d50f-4af0-8d24-bbff390ec424.png)


----------



### 0x02 公邮密码

下载文件得到压缩包，其中pw WINDoWsSEViCEss.txt文件为空，而公邮密码.zip文件需要解压密码，刚开始还以为pw WINDoWsSEViCEss.txt的文件被加密，后来才发现不是。用Winhex打开，没找到压缩包密码。就猜测可能是要爆破压缩包密码，把压缩包用Ziperello跑一下，得到密码为BIT，输入密码解压，得到Base64编码的字符串RmxhZzp7THkzMTkuaTVkMWYqaUN1bHQhfQ==，base64解码得到flag。


----------
### 0x03 说我作弊，需要证据

下载后得到数据包文件，丢到wireshark里分析，Follow stream后发现一堆base64加密后的字符串
![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/3901ae09-b602-43db-9a5b-03c8553c9e35.png)


![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/3901ae09-b602-43db-9a5b-03c8553c9e35.png)



github上原题
这题找到了原题[https://github.com/RandomsCTF/write-ups/tree/master/Hack.lu%20CTF%202015/Creative%20Cheating%20%5Bcrypto%5D%20(150)](https://github.com/RandomsCTF/write-ups/tree/master/Hack.lu%20CTF%202015/Creative%20Cheating%20%5Bcrypto%5D%20(150) ) ，直接运行脚本就拿到flag


----------

### 0x04 你猜猜。。

复制字符串到winhex里粘贴，得到一个加密的zip压缩包
![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/83ef3419-749a-4c62-adef-9b81c5c9b227.png)
使用工具爆破压缩包，得到解压密码为123456，解压得到flag.txt
![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/104896c0-dc81-4d97-b1a3-a439b14dd19a.png)

----------

### 0x05 神秘图片

binwalk分析一个图片，发现有两张，用命令分离一下出来，然后是一个猪圈密码，解密出来即可

分离图片的一些trick 见 http://www.tuicool.com/articles/VviyAfY 


----------

### 0x06 告诉你个秘密


	
636A56355279427363446C4A49454A7154****30526D6843
56445A31614342354E326C4B4946467A5769426961453067

将两串字符串进行16进制解密

	
cjV5RyBscDlJIEJqTSB0RmhC  
VDZ1aCB5N2lKIFFzWiBiaE0g

用base64解密得到

r5yG lp9I BjM tFhB T6uh  
y7iJ QsZ bhM

得到一串似乎毫无规律的字符串，但仔细看还是可以知道是键盘密码，在自己键盘上比划下就知道了,最终得到

	
tongyuan


----------
### 0x07 PHP_encrypt_1

题目的加密算法如下

![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/0c551a6d-7d69-4b6a-8aab-80e8d7e18f44.png)

提示题目提示可知加密算法是可逆的，就直接google了下相应的加密算法，找到几乎一样的PHP加解密算法的实现，链接地址为：http://www.ctolib.com/topics-25812.html




----------

### 0x08 二维码

扫描二维码，得到提示信息，flag是路由器的密码，通过binwalk分析图片发现有一个压缩包，使用binwalk -e 自动分离得到后发现需要密码,用 ziperello 爆破个八位数字，密码就出来了 , 然后得到一个cap的握手包，Kali Linux下使用aircrack-ng来跑包

aircrack -ng C8-E7-D8-E8-E5- 88_handshake.cap -w fuzz.txt

fuzz.txt 是自己写的一个生成字典的脚本


![](http://www.360zhijia.com/wp-content/uploads/2017/05/26/71727701-b5d5-4ee6-ac16-b55cc036f565.png)

最后跑出flag为 ： ISCC16BA