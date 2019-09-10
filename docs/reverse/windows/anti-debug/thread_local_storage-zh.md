[EN](./thread_local_storage.md) | [ZH](./thread_local_storage-zh.md)
# Thread Local Storage(TLS)

线程本地存储(TLS)用于在线程启动前对特定线程数据进行初始化, 因为每个进程都包含至少1个线程, 在主线程运行前初始化数据. 初始化操作可以通过指定一个已经复制到动态分配内存中去的静态缓冲区, 和/或通过在回调函数数组中执行代码, 来初始化动态内存内容. 经常是由于滥用回调函数数组而造成问题.

在运行时, TLS回调函数数组内容可以被修改或增加, 新加入或新修改的回调函数会使用新地址进行调用. 回调函数的数目也没有限制. 数组的扩展操作可以用以下代码完成:

``` asm
l1: mov d [offset cbEnd], offset l2
    ret
l2: ...
```

当l1处的回调返回时就会继续调用l2的回调函数

> todo: continue to finish it

