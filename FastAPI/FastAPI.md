# FastAPI中的QuickStart


```
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/")
async def home():
    return {"user_id": 1001} #创建返回值

@app.get("/shop")
async def home():
    return {"shop_id": 1002} #创建返回值

#不使用终端命令的uvicorn而直接点击运行的方式
if __name__ == "__name__":
    uvicorn.run("1.py:app", port = 8080, debug = True, reload = True)
```

# FastAPI中的路径操作装饰器方法参数简介
## 路径操作装饰器
FastAPI中的请求方法有：
```
@app.get()
@app.post()
@app.put()
@app.patch()
@app.delete()
@app.options()
@app.head()
@app.trace()
```
路径操作装饰器方法的参数
```
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.post("/items", tags = ["itmes测试接口“]， summary = ["itmes测试总结“])
async def home():
    return {"user_id": 1001} #创建返回值

#不使用终端命令的uvicorn而直接点击运行的方式
if __name__ == "__name__":
    uvicorn.run("1.py:app", port = 8080, debug = True, reload = True)
```
