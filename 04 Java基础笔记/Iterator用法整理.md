# Java Iterator 用法整理
--------

## Iterator  
迭代器，轻量级对象，它可以遍历并选择序列中的对象。  
常用方法：  

> next()  

获得序列中的下一个元素，第一次调用时，返回第一个元素  

> hasNext()  

检查序列中是否还有元素  

> remove()  

将迭代器新返回的元素删除  

## Iterator应用  

     list l = new ArrayList();
     l.add("aa");
     l.add("bb");
     l.add("cc");
     for (Iterator iter = l.iterator(); iter.hasNext();) {
         String str = (String)iter.next();
         System.out.println(str);
     }