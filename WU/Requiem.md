## KCSC/MISC

## Requiem

### Lời giải

```python
import socket


def toInt(string):
    val = ''
    a = '1234567890'
    for i in string:
        if i in a:
            val += i
    return val

# input nhận về luôn nằm dòng cuối nên mình cắt theo dòng r lấy số từ dòng cuối, code đẹp hơn có thể DP làm tối ưu thời gian cơ mà cái này mình nghĩ code ra flag là được.
def split(string):
    tmp = string.split("\n")
    return tmp


host = "103.162.14.116"
port = 14005
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_address = ((host, port))
s.connect(server_address)
a = 1
x = [0]*100000
x[0] = 1

while True:
    receive = s.recv(1024).decode("utf8")
    print(receive)
    receive = split(receive)
    k = receive[-1]
    if k != '':
        inp = int(toInt(k))

        if x[inp] != 0:
            print(x[inp])
        else:
            while a <= inp:
                if a % 2 == 0:
                    x[a] = x[a-1] * a
                else:
                    x[a] = x[a-1] + a
                a += 1
            print(x[inp])

        s.send(str(x[inp]).encode("utf8"))
s.close()
```

![Alt text](IMG/Req/image.png)

- cuối cùng ta cat file tmp.txt tìm flag với format đầu là KCSC{. bài này do ngắt sever rồi nên mình không thực hiện lại để lấy flag được.

```
flag: KCSC{}
```

## Mong WRITEUP này giúp ích cho các bạn!

```
from KMA
Author: 13r_ə_Rɪst
Email: sonvha2k23@cvp.vn
```
