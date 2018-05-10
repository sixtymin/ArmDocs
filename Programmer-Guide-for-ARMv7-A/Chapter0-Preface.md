
###前言###

据统计，在2014年移动电话的数量将超过人类数量；而这些移动设备中有大约90%使用ARM处理器。

这本书的目的就是向使用ARMv7-A架构的ARM Cortex-A系列处理器的编程人员提供ARM技术的介绍。这本书作为其他的ARM Cortex-A系列处理器文档的补充而非替代品，比如介绍处理器自身的文档ARM Technical Reference Manuals，单个设备或开发板的文档，或最重要的ARM ARM（即ARM Architecture Reference Manual）。

这本书的目的是像使用Cortex-A系列处理器开发应用的编程人员提供单一文档，本书从各种资料中整理了有助于汇编语言或C语言编程人员的信息。硬件概念，例如缓存（Caches）和内存管理单元（MMU），但是仅仅介绍对于程序编写有帮助的内容。文档也会包含操作系统，比如Linux，利用ARM功能的一些方法；以及如何最大程度地使用ARM处理器，特别是如何为多核处理器编写软件。

尽管本书的大部分内容对于老一些的ARM处理器依然可用，但是并没有刻意去覆盖实现老版本架构的处理器的编程信息。Cortex-R系列和M系列处理器也有提到但是并没有进行详细说明。我们的目的在于尽量以易于理解的方式介绍ARM架构，详细地介绍功能集以及为编写Cortex-A系列处理器上可以高效执行的C和汇编程序提供切实可行的建议。

这本书并不是一本入门级的书籍。阅读本书最好具有一些C语言编程和微处理器的知识，但对于ARM的知识背景并没有过多要求。当然了限于本书的目标与资源，我们也不可能详细解释每一个话题。一些章节中给出了额外的参考资料（可能是书或者网页），通过这些参考资料可以对章节中所讨论的主题有更深层次的学习，在这本书中我们仅仅集中介绍ARM特定的一些内容。书中没有强制使用任何特定的工具集，在本书的介绍过程中会提到GNU和ARM的工具。这本书适合于想要了解基于ARM处理器的编程，并且具有PC或X86桌面应用编程背景的人阅读。

第一章介绍了ARM Cortext-A系列CPU的基本功能。ARM架构的基本介绍，各种寄存器和模式，以及特定处理器的一些背景知识在第二章和第三章介绍。第四章和第五章简要介绍了ARM汇编语言ibancheng，详细介绍了汇编语言指令。在第六和第七章分别介绍浮点数和ARM的高级SIMD扩展（NEON）。这些章节仅仅是概要性地介绍这些内容。在第八，九和十章开始介绍内存系统，包括缓存（Caches），内存管理和内存序。异常和中断处理在第十一和十二章介绍。

本书余下的章节提供高级编程信息，第十三章介绍系统引导代码；第十四章介绍从其架构或老版本ARM架构向ARMv7-A上移植C和汇编代码的方法。第十五章介绍应用程序二进制接口，这对于C和汇编语言程序员都有用。代码的分析与优化在十六和十七章介绍。这里介绍的一些技术并不特定于ARM架构，但对于处理器特定的内容会给出提示。

第十八和十九章介绍多核处理器的内容。两章中会详细介绍ARM是如何实现多核的，以及如何编写代码来充分利用多核的性能。电源管理是ARM编程比较重要的部分，它会在二十章中进行讲解。最后一部分内容是第二十一章中介绍的ARM安全扩展（TrustZone），二十二章介绍的ARM虚拟化扩展，二十三章介绍的big.LITTLE技术以及二十四章介绍的硬件调试功能。附录A中给出了可用的ARM指令概述；附录B介绍使用ARM编程可用的一些工具和平台；附录C按照一步一步的方式给出了配置和编译RAM架构上的Linux操作系统。

###第四版前言###

ARM体系结构持续进化，ARM最近公布了ARMv8结构体系。ARMv8体系结构并不在本书中进行说明，但是对本书内容有一些影响。为了兼容ARMv8，ARMv7的指令接结构作了一些小的变化。这些变化在这一版中有体现。我们也利用这次机会完成对本书内容整体修订。

在阅读本书时会发现有一部分作了移动，一些作了扩展性地重写，一些只是做了微小改动。介绍相同内容的章节也被合并了。介绍寄存器的章节被大量改写，囊括了安全和虚拟扩展，以及权限级别的介绍。异常处理的章节进行内容整理，实现与ARMv8中介绍的一致性。类似的方法也被用于修改多处理器和并行化。在所有情况中，原来是两章内容的部分合并为一章，内容进行更新。LPAE现在则在虚拟化一章进行讲解。关于工具，操作系统和开发板的内容被移到了附录中，但是big.LITTLE技术被扩展修订为单独一章内容，以保持与快速变化技术的同步。

ARM增加了一个新的处理器到ARMv7 Cotex-A系列中，即新的Cortex-A12处理器，当然在本书中也进行介绍。你也会注意到之前对设备的称呼已经修改。处理器现在指市场上的处理器设备，例如Cortex-A15处理器，其他的地方则称为内核或内核集。

在老版本指南中的一些过时内容被删除了。例如NEON/VFP附录和编写NEON代码章节被删除。最初说NEON需要介绍它自己的单独一本书。现在确实有了，即ARM NEON Programmer’s Guide。

对于使用Cortex-A系列处理器的开发者，额外的信息以编程线索或提示的形式给出。尽管这些并不能覆盖到编程中遇到的每一个问题，但是我们希望本书的例子非常有用。

Cortex-A系列编程指南已经被证明是ARM文档集中非常流行的文档，它已经成为了ARM认证工程师考试的指定参考书。

###术语###

本书中使用的缩写和术语在这一部分进行定义。

|  术语   |     解释     |
|--------|--------------|
|AAPCS | ARM Architecture Procedure Call Standard，ARM架构过程调用标准|
|ABI   | Application Binary Interface，应用程序二进制接口|
|ACP   | Accelerator Coherency Port，加速器相关端口 |
|AEABI | ARM Embedded ABI，ARM嵌入式应用二进制接口|
|AHB   | Advanced High-Performance Bus，高级高性能总线|
|AMBA  | Advanced Microcontroller Bus Architecture，高级微处理器总线架构|
|AMP   | Asymmetric Multi-Processing，非对称多处理器技术 |
|APB   | Advanced Peripheral Bus，高级外围总线 |
|ARM ARM | The ARM Architecture Reference Manual，ARM架构参考手册 |
|ASIC    |Application Specific Integrated Circuit，专用集成电路 |
|APSR   | Application Program Status Register，应用程序状态寄存器 |
|ASID   | Address Space ID，地址空间ID |
|ATPCS  | ARM Thumb Procedure Call Standard，ARM Thumb过程调用标准 |
|AXI    | Advanced eXtensible Interface，高级可扩展接口 |
|BE8    | Byte Invariant Big-Endian Mode，字节不变大端模式 |
|BIU    | Bus Interface Unit，总线接口单元 |
|BSP    | Board Support Package，板级支持包 |
|BTAC   | Branch Target Address Cache，分支目标地址缓存 |
|BTB    | Branch Target Buffer，分支目标缓存 |
|CISC   | Complex Instruction Set Computer，复杂指令集计算机 |
|CP15   | Coprocessor 15. System control coprocessor，15号协处理器，系统控制协处理器|
|CPSR   | Current Program Status Register，当前程序状态寄存器 |
|DAP    | Debug Access Port，调试访问端口 |
|DBX    | Direct Bytecode Execution，直接字节码执行 |
|DDR    | Double Data Rate (SDRAM)，双数据率 |
|DMA    | Direct Memory Access，直接内存访问 |
|DMB    | Data Memory Barrier，数据内存栅栏 |
|DPU    | Data Processing Unit，数据处理单元 |
|DS-5   | The ARM Development Studio，ARM开发工具包 |
|DSB    | Data Synchronization Barrier，数据同步栅栏 |
|DSP    | Digital Signal Processing，数字信号处理 |
|DSTREAM| An ARM debug and trace unit，RAM调试和追踪单元 |
|DVFS   | Dynamic Voltage/Frequency Scaling，动态电压/频率调节 |
|EABI   | Embedded ABI，嵌入式ABI |
|ECC    | Error Correcting Code，错误纠正码/纠错码 |
|ECT    | Embedded Cross Trigger，嵌入式交叉触发 |
|EOF    | End Of File，文件结束符 |
|ETB    | Embedded Trace Buffer，嵌入式追踪缓存 |
|ETM    | Embedded Trace Macrocell，嵌入式追踪微单元 |
|FDT    | Flattened Device Tree，扁平设备树 |
|FIQ    | An interrupt type (formerly fast interrupt)，一种终端类型，快速中断 |
|FPSCR  | Floating-Point Status and Control Register，浮点数状态和控制寄存器 |
|GCC    | GNU Compiler Collection，GNU编译器集 |
|GIC    | Generic Interrupt Controller，通用中断控制器 |
|GIF    | Graphics Interchange Format，图形交换格式，一种图片格式 |
|GPIO   | General Purpose Input/Output，通用输入输出 |
|Gprof  | GNU profiler，GNU分析其 |
|Harvard architecture | 哈佛架构，具有数据和指令分离存储，单一总线的CPU体系结构 |
|HCR    | Hyp Configuration Register，Hyp配置寄存器 |
|HMP    | Heterogenous Multi-Processing，异构多处理器 |
|ICU    | Instruction Cache Unit，指令缓存单元 |
|IDE    | Integrated development environment，集成开发环境 |
|I/F    | Interface，一些图中接口的缩写 |
|IPA    | Intermediate Physical Address，中间物理地址 |
|IRQ    | Interrupt Request，中断请求，通常是外部中断 |
|ISA    | Instruction Set Architecture，指令集架构 |
|ISB    | Instruction Synchronization Barrier，指令同步栅栏 |
|ISR    | Interrupt Service Routine，中断服务例程 |
|Jazelle| The ARM bytecode acceleration technology，ARM字节码加速技术 |
|JIT    | Just In Time，即时编译 |
|L1/L2  | Level 1/Level 2，一级缓存/二级缓存 |
|LPAE   | Large Physical Address Extension，大物理地址扩展 |
|LSB    | Least Significant Bit，最低有效位 |
|MESI   | 带有四个状态的缓存协议，修改，执行，共享，无效 |
|MMU    | Memory Management Unit，内存管理单元 |
|MOESI  | 带有五个状态的缓存协议，修改，占有，独有，共享和无效 |
|MPU    | Memory Protection Unit，内存保护单元 |
|MSB    | Most Significant Bit，最高有效位 |
|NEON   | The ARM Advanced SIMD Extensions，ARM高级单指令多数据扩展 |
|NMI    | Non-Maskable Interrupt，非可屏蔽中断 |
|Normal world | 内核在非安全状态时的执行环境 |
|Oprofile| A Linux system profiler，Linux系统分析器 |
|QEMU   | A processor emulator，一个处理器模拟器 |
|PCI    | Peripheral Component Interconnect，外围组件互联，计算机总线标准 |
|PCS    | Procedure Call Standard，过程调用标准 |
|PFU    | Prefetch Unit，预取单元 |
|PIPT   | Physically Indexed, Physically Tagged，物理索引，物理标记|
|PLE    | Preload Engine，预加载引擎 |
|PLI    | Preload Instruction，预加载指令 |
|PMU    | Performance Monitor Unit，性能监控单元 |
|PoC    | Point of Coherency， 一致点 |
|PoU    | Point of Unification，统一点 |
|PPI    | Private Peripheral Input，私有外围输入 |
|Privilege | 不能从用户（无特权的）模式执行特定任务的能力 |
|PSCI   | Power State Coordination Interface，电源状态协调接口 |
|PSR    | Program Status Register，程序状态寄存器 |
|RCT    | Runtime Compiler Target，运行时编译器目标 |
|RISC   | Reduced Instruction Set Computer，精简指令集计算机 |
|RVCT   | RealView Compilation Tools，ARM编译器 |
|SBZP   | Should Be Preserved，被保留 |
|SCU    | Snoop Control Unit， 监控控制单元 |
|Secure world | 当内核处于安全状态是的执行环境 |
|SGI    | Software Generated Interrupt，软件生成中断 |
|SIMD   | Single Instruction, Multiple Data，单指令多数据 |
|SiP    | System in Package，包中系统 |
|SMP    | Symmetric Multi-Processing， 非对称多处理器 |
|SoC    | System on Chip，片上系统 |
|SP     | Stack Pointer，栈指针 |
|SPI    | Shared Peripheral Interrupt，共享外围中断 |
|SPSR   | Saved Program Status Register，保存的程序状态寄存器 |
|Streamline | A graphical performance analysis tool，一个图形性能分析工具 |
|SVC    | Supervisor Call instruction，访指令，以前是SWI |
|SWI    | Software Interrupt instruction，软件中断指令，有SVC代替 |
|SYS    | System Mode，系统模式 |
|TAP    | Test Access Port，测试访问端口，JTAG接口 |
|TDMI   | Thumb, Debug, Multiplier, ICE|
|TEX    | Type Extension，类型扩展 |
|Thumb  | ARM的扩展指令集 |
|Thumb-2| 扩展Thunb指令集，支持16位和32位指令集 |
|TLB    | Translation Lookaside Buffer，转换旁路缓存 |
|TLS    | Thread Local Storage，线程局部存储 |
|TrustZone | The ARM security extension，ARM安全扩展 |
|TTB    | Translation Table Base，转换表基地址 |
|TTBR   | Translation Table Base Register，转换表基址寄存器 |
|UAL    | Unified Assembly Language，统一汇编语言 |
|UART   | Universal Asynchronous Receiver/Transmitter，通用异步接收/发送器 |
|UEFI   | Unified Extensible Firmware Interface，统一可扩展固件接口 |
|U-Boot | A Linux Bootloader，一个Linux引导加载器 |
|UNK    | Unknown，未知 |
|USR    | User mode, a non-privileged processor mode，用户模式，一个非特权处理器模式|
|VFP    | ARM浮点指令集，在ARMv7以前VFP扩展被称为向量浮点架构，用于向量操作 |
|VIC    | Vectored Interrupt Controller，中断向量控制器 |
|VIPT   | Virtually Indexed, Physically Tagged，虚拟索引，物理标记 |
|VMID   | Virtual Machine ID，虚拟机器ID |
|VMSA   | Virtual Memory Systems Architecture，虚拟内存系统结构 |
|XN     | Execute Never，从不执行 |

###排版约定###

本书使用如下的排版约定：

**斜体**：强调重要注释，介绍特定的术语，解析内部交叉引用以及引用文字。
**粗体**：描述列表中标识术语。
**单行间隔**：表示可以在键盘上输入的的文本，例如命令，文件和程序名字，指令名字，参数和源码。
**单行间隔斜体**: 表示单行间隔出来文本的参数，需要指定特定值的参数。
**< 和 >**: 括住汇编语法中可替代的项目，一般出现在代码或代码片段中，例如`MRC p15, 0, <Rd>, <CRn>, <CRm>, <Opcode_2>`

###反馈###

我们已经尽量确保`Cortex-A Series Programmer's Guide`既易于阅读与理解，同时也按照我们最初期望的那样提供有足够深度且全面介绍的资料。

如果有任何个人意见，不理解我们的解释，丢失了什么内容或哪些内容不正确，发邮件到`errata@arm.com`。给出如下信息：

* 题目写`The Cortex-A Series Programmer’s Guide`。
* 编号写`ARM DEN0013D`。
* 要评论的内容的页码。
* 你想要看到修改的内容。

ARM也欢迎您提出增加内容或改进方面的其他建议。

###参考文献###

* Cohen, D. “On Holy Wars and a Plea for Peace”, USC/ISI IEN April, 1980 http://www.ietf.org/rfc/ien/ien137.txt.
* Furber, Steve. “ARM System-on-chip Architecture”, 2nd edition, Addison-Wesley, 2000, ISBN: 9780201675191.
* Hohl, William. “ARM Assembly Language: Fundamentals and Techniques” CRC Press, 2009. ISBN: 9781439806104.
* Sloss, Andrew N.; Symes, Dominic.; Wright, Chris. “ARM System Developer's Guide: Designing and Optimizing System Software”, Morgan Kaufmann, 2004, ISBN: 9781558608740.
* ANSI/IEEE Std 754-1985, "IEEE Standard for Binary Floating-Point Arithmetic".
* ANSI/IEEE Std 754-2008, “IEEE Standard for Binary Floating-Point Arithmetic”.
* ANSI/IEEE Std 1003.1-1990, “Standard for Information Technology - Portable Operating System Interface (POSIX) Base Specifications, Issue 7”.
* ANSI/IEEE Std 1149.1-2001, “IEEE Standard Test Access Port and Boundary-Scan Architecture”.
* ANSI/IEEE Std 1275-1994, “IEEE Standard for Boot Firmware (Initialization Configuration) Firmware: Core Requirements and Practices”.
* The ARM Architecture Reference Manual(即the ARM ARM)对于认真的ARM程序员来说是必读的文档。在ARM的官网上可以下载。它完整描述了ARMv7的指令集架构，编程模型，系统寄存器，调试功能和内存模型。它描述了详细的规范，所有的ARM处理器必须遵守。这本书中参考的架构参考文档是ARM Architecture Reference Manual - ARMv7-A and ARMv7-R edition (ARM DDI 0406).
* ARM Generic Interrupt Controller Architecture Specification version 2.0 (ARM IHI 0048).
* ARM Compiler Toolchain Assembler Reference (DUI 0489).
* ARM C Language Extensions (IHI 0053).
* ARM NEON Programmer’s Guide (DEN 0018).
* Procedure Call Standard for the ARM Architecture (ARM IHI 0042).
* Power State Coordination Interface (PSCI) Platform Design Document (ARM DEN 0022)

特定处理器的技术参考文档为处理器行为提供了详细描述。从ARM网站文档区（http://infocenter.arm.com）可以获取这些文档。


