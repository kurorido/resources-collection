
# HandlerThread & Looper & IntentService & MessageQueue
* http://www.cnblogs.com/lqminn/p/3795636.html
* http://www.cnblogs.com/lqminn/p/3751820.html

IntentService 其實只是使用 HandlerThread 的一個實際例子

內部的 ServiceHandler 使用 onCreate 中建立的 HandlerThread 的 Looper 來達到非同步工作

```
HandlerThread thread = new HandlerThread("IntentService[" + mName + "]");
thread.start();

mServiceLooper = thread.getLooper();
mServiceHandler = new ServiceHandler(mServiceLooper);
```

Looper prepare 會初始化 Looper 並且建立 MessageQueue 和關聯現在的 Thread
Looper只是负责管理消息队列，也就是取出消息进行处理，而Handler则是负责发送消息以及处理消息的

Looper 透過 sThreadLocal.get 來取得現在的 Looper

```
public static Looper myLooper() {
    return sThreadLocal.get();
}
```

Handler 預設建構子是非 async 的，但事實上可以帶給參數變成 async

```
public Handler() {
    this(null, false);
}

public Handler(Callback callback, boolean async) {
    .... // 取用現在的 looper
}

public Handler(Looper looper, Callback callback, boolean async) {
    .... // 指定特定的 looper
}
```

所有的 sendMessage, sendEmptyMessage, sendEmptyMessageDelayed 都會導到

```
public boolean sendMessageAtTime(Message msg, long uptimeMillis) {
```

Looper.loop 當中有一個無窮 for loop 等待 message queue 裏頭的 message 進來

```
msg.target.dispatchMessage(msg)
```
