**Thresh** là một phần của **Processing**. Các **thresh** trong 1 chương trình không chạy cùng 1 thời điểm mà swap qua lại(Concurrent: core to thread)

- Nếu không thêm join vào code khi start 2 thread
```python
import threading
import time

def test(name):
    print(f"Hello {name}")
    time.sleep(1)
    print(f"{name} finished")

#Create thread
thread1 = threading.Thread(target=test, args=("Thread 1",))
thread2 = threading.Thread(target=test, args=("Thread 2",))
#Start thread
thread1.start()
thread2.start()
#Count num of thread
print("Num of threads: ", threading.active_count())

# thread1.join()
# thread2.join()
print("Heluu")
```
- **Kết quả**
```
Hello Thread 1
Hello Thread 2
Num of threads:  3
Heluu
Thread 1 finished
Thread 2 finished
```
---
- Khi thêm join vào đoạn code với mục đích khiến 2 thread1 và thread2 chạy xong mới thưc hiện đoạn in "Heluu"
```python
import threading
import time

def test(name):
    print(f"Hello {name}")
    #time.sleep(1)
    print(f"{name} finished")

#Create thread
thread1 = threading.Thread(target=test, args=("Thread 1",))
thread2 = threading.Thread(target=test, args=("Thread 2",))
#Start thread
thread1.start()
thread2.start()
#Count num of thread
print("Num of threads: ", threading.active_count())

thread1.join()
thread2.join()
print("Heluu")
```
- **Kết quả**
```
Hello Thread 1
Hello Thread 2
Num of threads:  3
Thread 1 finished
Thread 2 finished
Heluu
```

# Request API
```python
import threading
import time
import requests
import logging

def test(index):
    response = requests.get("https://api.coindesk.com/v1/bpi/currentprice.json")
    logging.info(f"{response}")
    #logging.info(f"Request {index}")

if __name__ == "__main__":
    logging.basicConfig(level=logging.INFO,
                        format="%(asctime)s %(message)s",
                        datefmt="%Y-%m-%d %H:%M:%S",
                        handlers = [
                            logging.StreamHandler(),
                            logging.FileHandler("test.log")
                        ])

    # """ 22.02s """
    # start = time.time()
    # for i in range(1000):
    #     test(i)
    # logging.info(f"Time: {time.time() - start}")

    start = time.time()
    list_thread = []
    for i in range(1000):
        list_thread.append(threading.Thread(target=test, args=(i,)))

    for i in range(1000):
        list_thread[i].start()

    for i in range(1000):
        list_thread[i].join()
    logging.info(f"Time: {time.time() - start}")

```
- **So sánh kết quả**

| Step | Normal | Threading |
|---| ---|---|
| 100 | 22.02s | 1.19s |
| 1000 | 224.33 | 10.81s | 

