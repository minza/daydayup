# 为什么需要base64

原因是因为有些字节在传输过程中受限（控制字符），为了让这些字节可以传输，用可见字符对他们进行二次编码

> 控制字符，可见字符

控制字符是用来控制行为（空格、回车之类的）和用来通讯用的专用字符，ascll中的控制字符有34个
可见字符是能够在键盘上输入，可以被打印出来的的字符

> *base64编码原理*

大家知道ascll中一个字节表示一个字符，数字。而计算机中一个字节有8个bit。base64用了64个字符（a-z，A-Z，0-9，+，/）作为字符表，64个字符只是2的6次方，意思是只需要6个bit就能表示一个在编码表中的字符了，编码的原理就是吧普通字节的二进制数按照6个一组抽出来，再对比编码表取出字符

> 浏览器中的使用方法
```
var str = 'somestr'
window.btoa(str)  //base64转码
window.atob(str)  //base64解码
```

> 需要注意

因为base64是6个bit,普通字节是8bit，最小公倍数是24，所以3个普通字节可以被base完整表达，小于三个字节的编码出来之后会自动补1到2个=