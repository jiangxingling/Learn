# Python 文件读写  
----------------------

## 写文件  
使用 write() 函数  

    f = open('test.txt','a+')
    f.write("add line"+'\n')
    f.close()  

每次写完文件后都需要调用 close() 关闭文件，但是一旦前面的过程出错，close() 语句就不会执行，所以需要使用 try ... finally:  

    try:
        f = open('test.txt','a+')
        f.write("add line"+'\n')
    finally:
        if f:
            f.close()  

但是这样写比较繁琐，所以可以通过 with 语句来自动调用 close()：  

    with open('test.txt','a+', encoding='utf-8-sig') as f:
        f.write("this is a text file")  

## 读文件  

    with open('test.txt','r', encoding='utf-8-sig') as f:
        print(f.read())


## 附：文件操作权限  

> w     以写方式打开，  
> a     以追加模式打开 (从 EOF 开始, 必要时创建新文件)  
> r+     以读写模式打开  
> w+     以读写模式打开 (参见 w )  
> a+     以读写模式打开 (参见 a )  
> rb     以二进制读模式打开  
> wb     以二进制写模式打开 (参见 w )  
> ab     以二进制追加模式打开 (参见 a )  
> rb+    以二进制读写模式打开 (参见 r+ )  
> wb+    以二进制读写模式打开 (参见 w+ )  
> ab+    以二进制读写模式打开 (参见 a+ )  