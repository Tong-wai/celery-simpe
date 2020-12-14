使用celery 创建任务用flower监控



```
1.启动redis
2.启动celery任务
celery -A proj.app_test worker -l info
3.启动flower
flower -A proj.app_test beat
4.启动任务
python diaoyong.py
```

在浏览器中 localhost:5555 查看任务

我们一次性调用了五次add函数，但是运行的总时间才1.298691034317017秒多。这是celery异步运行的结果，如果是同步运行，那么，至少需要5秒多，因为每调用add函数一次，就会休眠一秒

