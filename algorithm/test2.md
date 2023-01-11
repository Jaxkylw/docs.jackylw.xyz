# （2009-42）已知一个带有表头结点的单链表，结点结构为：

| Data | Link |
| ---- | ---- |

假设该链表只给出了头指针 list。在不改变链表的前提下，请设计一个尽可能高效 的算法，查找链表中倒数第 k 个位置上的结点（k 为正整数）。若查找成功，算法 输出该结点的 data 域的值，并返回 1；否则，只返回 0。要求： 

## 1. 描述算法的基本设计思想。 
## 2. 描述算法的详细实现步骤。 
## 3. 根据设计思想和实现步骤，采用程序设计语言描述算法（使用 C、C++或 Java 语言实现），关键之处请给出简要注释

***

解析:

1. 定义两个指针变量 p 和 q，初始时均指向头 结点的下一个结点（链表的第一个结点）。p 指针沿链表移动；当 p 指针移动到第 k 个结点时，q 指针开始与 p 指针同步移动；当 p 指针移动到最后一个结点时，q 指针 所指示结点为倒数第 k 个结点。以上过程对链表仅进行一遍扫描。

2. ①count=0，p 和 q 指向链表表头结点的下一个结点； ②若 p 为空，转⑤； ③若 count 等于 k，则 q 指向下一个结点；否则，count=count+1； ④p 指向下一个结点，转②； ⑤若 count 等于 k，则查找成功，输出该结点的 data 域的值，返回 1；否则，说明 k 值超过了线性表的长度，查找失败，返回 0； ⑥算法结束。

3. ```c
   typedef int ElemType; ∥链表数据的类型定义
   typedef struct LNode{ ∥链表结点的结构定义
   ElemType data; ∥结点数据
   struct Lnode *link; ∥结点链接指针
   } *LinkList;
   
   int Search_k(LinkList list, int k){
   LinkList p = list->link, q = list->link; ∥指针 p、q 指示第一个结点
   int count = 0;
   while(p != NULL){ ∥遍历链表直到最后一个结点
   if(count < k) count++; ∥计数，若 count < k 只移动 p
   else q = q->link;
   p = p->link; ∥之后让 p、q 同步移动
   } ∥while
       
   if(count < k)
   return 0; ∥查找失败返回 0
   else{ ∥否则打印并返回 1
   printf(“%d”,q->data);
   return 1;
   }
   } ∥Search
   ```

