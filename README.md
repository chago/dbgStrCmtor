# dbgStrCmtor

最近因为研究内容的关系,需要经常分析加固和混淆过的elf文件.真是比较耗费精力的事情啊.<br />特别是ida pro与od不一样的, 寄存器窗口不会直接把字符串显示出来.所以,经常需要双击地址,再双击地址一直到一个字符串. 才知道当前在处理什么文件,或者处理什么内容. <br />
函数更是这样了,初步调试很多函数看到入参和出参就能猜到函数功能了. 双击再双击是在麻烦, 如果能在每个调用函数的时候能直接看到入参和出参就好了. <br />
我们对于一些常见的Hash函数(SHA1,MD5等),加解密函数(AES等), 通常是通过一些常量和一些固定的汇编逻辑来识别的. 如果能比较快速的识别出来哪些代码在运行的是Hash函数/加解密函数的逻辑,也能节省很多调试时间. <br />
于是做了这么一个程序. 包含三个功能点:
<br />
1.	识别字符串,以及字符串的指针(或者多层指针最终指向一个字符串),并且把字符串内容以comment的形式附加到指令处.
<br />
2.	记录函数入参与出参,并且以comment的形式附加到函数的调用处. 
<br />
3.	识别各种常见的Hash函数以及加解密函数(的常量),并且以comment形式附加到识别出来的指令处. 


最后说一下怎么用:<br />
两种加载方式:<br />
 1. Ida pro->File->Script File<br />
 2. 直接把这个文件放到 ida pro安装目录的plugins目录里面. <br />
加载完成以后,使用快捷键: alt-2 开启上述插件功能. <br />
之后快捷键`-1, 是单步进入(Step Into). (请注意ida pro6.8以下版本请不要使用这个功能,因为有一个ida pro软件有个bug会导致崩溃, 6.8版本才修复好)<br />
快捷键`-2, 是单步步过 (Step Over). <br />
(`键是esc下面的那个键, 上面有~和`两种符号. )<br />

