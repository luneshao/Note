# Base64

(原文链接)['https://blog.csdn.net/wanlixingzhe/article/details/7107923']

[原文链接]('http://www.cnblogs.com/hongru/archive/2012/01/14/2321397.html')

## Base64

1字=2字节(1 word = 2 byte) 

1字节=8位(1 byte = 8bit) 

--------------------- 

* base64的编码都是按字符串长度，以每3个8bit的字符为一组;

* 然后针对每组，首先获取每个字符的ASCII编码;

* 然后将ASCII编码转换成8bit的二进制，得到一组3*8=24bit的字节;

* 然后再将这24bit划分为4个6bit的字节，并在每个6bit的字节前面都填两个高位0，得到4个8bit的字节;

* 然后将这4个8bit的字节转换成10进制，对照Base64编码表 （下表），得到对应编码后的字符。
