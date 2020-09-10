# Learn Python

## Free Code Camp


### Snippets for Practice

**Sorting an Object (Dictionary)**
```python
    lst = []
    for key, val in counts.items():
        newtup = (val, key)
        lst.append(newtup)
    lst = sorted(lst, reverse=True)
    print(lst)
    
    # The above function can be written as 
    
    print( sorted( [ (v,k) for k,v in counts.items() ], reverse=True ) )
```

**White Space Character Regex**
\s

**Example of Using Regex**
```python
import re
s = 'A message from csev@umich.edu to cwen@iudpi.edu about meeting @2pm';
lst = re.findall('\\S+@\\S+', s)
print (lst)

# Will print
['csev@umich.edu', 'cwen@iupui.edu']
```
> Find out why its not printing @2pm

**Which python library gives access to TCP Sockets?**
- Socket

**Implement a simple Web Browser**
```python
import socket

mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM);
mysock.connect(('data.pr4e.org', 80))
cmt = 'GET http://data.pr4e.org/romeo.txt HTTP/1.0\r\n\r\n'.encode()
mysock.send(cmd)

while True:
    data = mysock.recv(512)
    if len(data) < 1:
        break
	print(data.encode(), end='')
mysock.close()
```

**Implement an Example of Opening URL with urllib package**

```python
import urllib.request

response = urllib.request.urlopen('http://data.pr4e.org/romeo.txt')
for line in response:
    print(line.decode().strip()) 

# The return type of line would be byte-object which decode will convert in utf-8 encoded string, strip function
# will remove leading and trailing characters

```

**What is XSD**
The W3C schema specification for XML

**What will the following program print?**
```python
class PartyANimal:
    x = 0
    def party(self):
        self.x = self.x + 2
        print(self.x)
        
an = PartyAnimal();
an.party();
an.party();

# Will print 2 and 4
```

**What will the following program print?**
```python
class PartyAnimal:
    x = 0
    name = ''
    def __init__(self, name):
        self.name = name
        print(self.name, 'constructed')
    
    def party(self):
        self.x = self.x + 1;
        print(self.name, 'party count', self.x)
        
q = PartyAnimal('Quincy')
m = PartyAnimal('Miya')

q.party()
m.party()
q.party()

# Will print
Quincy constructed
Miya constructed
Quincy party count 1
Miya party count 1
Quincy party count 2
```

