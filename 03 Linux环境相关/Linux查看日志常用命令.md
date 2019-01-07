# Linux 查看日志常用命令
-----

> -f 实时打印日志  
> -n 显示行号

### tail 
> tail -f xx.log  实时打印日志文件  
> tail -n 10 xx.log  打印最后10行日志  
> tail -n +10 xx.log  打印后10行及其以后的日志  

### head  
> head -n 10 xx.log  打印前10行日志  

### cat 
> cat -n xx.log  查看日志 

### grep
> grep "keyword"  根据关键字查询 

### more 
分页打印（空格翻页）

### > xx.txt 
将日志保存到文件中

### 实例  
> cat -n xx.log ｜ grep "xx_Error"  查询关键字所在行号（假设在第10行）  
> cat -n xx.log | tail -n +10 | head -n 20 ｜more 翻页打印关键字后20行的日志  
> cat -n xx.log | tail -n +10 | head -n 20 > xx.txt  将关键字后20行的日志输出到文件中