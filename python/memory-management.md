# 内存管理

内存管理 分为4层 


第一层 封装c库  malloc realloc  free  避免不同平台的调用不一致，进行统一封装


第二层 内存池  block   pool arena 
