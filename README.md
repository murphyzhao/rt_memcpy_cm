# rt_memcpy Cortex-M 汇编加速版

## 适用平台：Cortex-M 3/4/7

汇编代码质量有保证，这个是Silicon即uCOS母公司的代码，在uCOS上已经用了十多年，用汇编加速rt_memcpy函数的主要原因并不是因为汇编本身比c语言快，而是在ARM指令中有一个 LDMIA STMIA指令，通过这两条指令，一次就可以读取/写入40个字节，极大的加速了拷贝过程。已经适配了KEIL GCC IAR三个平台。**汇编代码内部考虑到了地址非四字节需要对齐的情况**。



## 测试结果

keil环境下 10000个字节复制一万次 

rt_memcpy为1261ms 

本汇编版本为883ms

C库memcpy为906ms

---

在亮牛 LN882H 平台上的测试结果：

测试 10 万次，拷贝大小为 4096+777 字节的结果：

```
优化等级  代码运行位置   汇编版本   keil microlib 版本
 -O1        flash运行   1.849s    6.887s
```

测试 1 万次，拷贝 10000 字节的结果：

```
优化等级  代码运行位置   汇编版本   keil microlib 版本
 -O1        flash运行   382.170ms 1.410s
```

## 如何获取软件包

```
 RT-Thread online packages  --->
    system packages  --->
        enhanced kernel services --->
            [*] rt_memcpy_cm: Cortex-M kernel assembly accelerated version of rt_memcpy function
```



## 维护

[Meco Man](https://github.com/mysterywolf)
