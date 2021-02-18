# 内存管理

内存管理 分为4层 


第一层 封装c库  malloc realloc  free  避免不同平台的调用不一致，进行统一封装


第二层 内存池  block   pool arena 

## block

block可以分为8, 16 。。。 , 256，这些类型

## pool 
4k大小
freeblock   初始化后freeblock指向第一个block
nextoffset  下一个可用的block的偏移，pool初始化后执行第二个block
maxoffset   最后一个block的偏移，限制 nextoffset
使用后的block被释放后，挂到freeblock，block对应内存的前面一部分值记录下一个空闲block的地址，从而将所有的空闲block连起来

## arena
256k大小
arenas  数据记录所有arena_object
usable_arena_objects,  unused_arena_objects
usedpool
所有的pool为空， arena 可以回收
## 垃圾收集
分代（三代），垃圾检测，垃圾清理 ， 标记清楚，引用计数

gc_head  gc_ref减一  循环引用  
