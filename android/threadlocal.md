# Thread Local
* http://www.cnblogs.com/lqminn/p/3751206.html

在 Thread 外部有一 ThreadLocal 變數

```
public static ThreadLocal<Integer> intLocal = new ThreadLocal<Integer>() {
```

在 Thread 中引用
```
class MyThread extends Thread {
  @Override
  public void run() {
    System.out.println("Thread-" + id + " : " + intLocal.get());
    .... 
```

這個 intLocal 變數會是每個 Thread 獨立擁有自己一個
