## ARM文档阅读

关于ARM的书籍不多，详细且有深度的更少了。这其中的可能原因是ARM的官方文档太详细了，写任何书籍都显得略弱。

对于英文水平不太好的我阅读这些文档也略费劲！尽管水平不高，还是将阅读后的内容做简略记录，算是内容翻译（不完全对应，有添加部分个人理解内容）。对于ARM的技术文档有这么几个，针对特定CPU的`Technical Reference Manual`；针对CPU架构的`Architecture Reference Manual`；以及针对编程人员的指南`Programmer's Guide`，当然还有其他的零碎文档不一一表述了。对于编程人员来说，最先要了解的就是针对编程人员的编程指南了，所以这个工程就从`Programmer's Guide`开始。

每一本文档的翻译内容对应有一个目录，用Markdown文档记录，便于进行编辑与排版。PDF目录下为ARM官方文档，文档名称以及内容列举如下：

**1. ARM文档库（infocenter）**

几乎ARM的所有文档都可以在这个网站上找到，权威数据；同时对于每一份文档都会提供相应的PDF版本下载（备着以后下载文档时容易找连接）。

官方网址：[http://infocenter.arm.com/](http://infocenter.arm.com/)

**2. Cortex-A Series Programmer's Guide for ARMv7-A.pdf**

Cortex-A系列处理器的编程指南，针对ARMv7-A架构体系。

官方网址: [http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.den0013d/index.html](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.den0013d/index.html)

**3. Cortex-A Series Programmer's Guide for ARMv8-A.pdf**

Cortex-A系列处理器编程指南，针对ARMv8-A架构体系，相比于`for ARMv7-A`的文档，这本文档只介绍了增量内容。它只包含了AArch64的内容，而对于之前的内容还需要参考老版本文档。

官方网址: [http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.den0024a/index.html](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.den0024a/index.html)

**4. Procedure Call Standard for the ARM Architecture**

AAPCS.pdf/AAPCS64.pdf

**5. ARM C Language Extensions**

**6. ARM NEON Programmer’s Guide.pdf**

**7. ARM Compiler Toolchain Assembler Reference**

**8. Thumb-2 Supplement Reference Manual.pdf**

By Andy @2018-05-10