### 使用celery创建任务用supervisord 监控 flower 和 celery



```
手动执行：
1.启动redis
2.启动celery任务
cd cd ~/test/celery-simpe
celery -A proj.app_test worker -l info
3.启动flower
cd cd ~/test/celery-simpe
flower -A proj.app_test beat
4.启动任务
python diaoyong.py
```

```
cd ~/test/celery-simpe/proj
supervisord -c supervisord.conf

```

在浏览器中 localhost:5555 查看flower web页面
在浏览器中 localhost:9001 查看supervisor web页面

我们一次性调用了五次add函数，但是运行的总时间才1.298691034317017秒多。这是celery异步运行的结果，如果是同步运行，那么，至少需要5秒多，因为每调用add函数一次，就会休眠一秒

