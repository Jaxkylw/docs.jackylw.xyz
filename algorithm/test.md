# 123
## 顺序表
## 1222222
## 12222222222

### 静态分配

```c
#define MaxSize 100//定义最大长度
typedef struct{
    ElemType data[MaxSize];
    int length;//定义顺序表当前长度
}SeqList;//定义顺序表类型
```

### 动态分配

```c
#define InitSize 10//定义初始长度
typedef struct{
    ElemType *data;//分配数组指针
    int MaxSize;//定义最大长度
    int length;//定义顺序表当前长度
}SeqList;//定义顺序表类型
```