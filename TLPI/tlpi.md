## 25  进程的终止
### 25.1 _exit() 和exit()
进程终止的方式：
* 异常(abnormal) 产生coredump
* _exit()系统调用
```
# include <unistd.h>
void _exit(int status)
 ```
可用EXIT_SUCCESS(0)和EXIT_FAILURE(1)表示退出状态 
多数使用库函数
```
# include <stdlib.h>
void exit(int status)
```
exit()会执行如下动作
* 调用退出处理程序(通过atexit()和on_exit()注册的函数)，其执行顺序与注册时相反。
* 刷新stdio流缓冲区
* 使用有status提供的值执行_exit()系统调用

