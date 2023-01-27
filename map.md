🌟 HashMap 

    - key-value: key相当于value的一个描述或者引用
    - Map是通过get()获取对应的value，通过values()获取所有的value，而且还可以通过put进行新增键值对
    - 基于哈希表的Map接口实现
    - 底层是array结构
    - 无序，key值不可重复

intitialization:

    - Map< , > map = new HashMap<>();
    - HashMap map = new HashMap();      // 290

🌟TreeMap   

     - Map接口的基于Tree结构的实现
     - 基于红黑树实现[ ](https://github.com/julycoding/The-Art-Of-Programming-By-July/blob/master/ebook/zh/03.01.md)
     - 有序，key值可重复
     - comparator 排序[ ](https://www.liaoxuefeng.com/wiki/1252599548343744/1265117109276544)

🌟Pair<key, value> 

     - Pair保存的是一个信息对，key和value都要保存具体信息，也就是没有key和value之分
     - (不同点)
           - Pair保存的是一对key-value, 而map可以保存多对key-value
           - Pair通过getKey()/getValue()获取对应的key值和value值，没有添加键值对的操作
           - 



