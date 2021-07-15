**Thresh** là một phần của **Processing**. Các **thresh** trong 1 chương trình không chạy cùng 1 thời điểm mà swap qua lại

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