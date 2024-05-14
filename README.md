# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
All commands related to Network configuration which includes how to switch to privilege mode
and normal mode and how to configure router interface and how to save this configuration to
flash memory or permanent memory.
This commands includes
• Configuring the Router commands
• General Commands to configure network
• Privileged Mode commands of a router 
• Router Processes & Statistics
• IP Commands
• Other IP Commands e.g. show ip route etc.
## Program
### CLIENT:
```import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
while True:
    c,addr=s.accept()
    print("Connecting from ",addr)
    try:
        hostname=c.recv(1024).decode().strip()
        if hostname:
            try:
                response=str(ping(hostname,verbose=True))
                c.send(response.encode())
            except Exception as e:
                c.send("ping failed  {}".format(e).encode())
        else:
            c.send("Hostname not provided".encode())
    except Exception as e:
        print("Error: ",e)
    finally:
        c.close()
```
### SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
    while True:
        ip= input("Enter Website u want to ping :")
        s.send(ip.encode())
        response=s.recv(1024).decode()
        if response:
            print ("Ping result :",response)
        else:
            print ("No response from server")
except Exception as e:
    print ("Error:", e)
finally:
    s.close()
```
### TRACEROUTE COMMAND:
```from scapy.all import* 
target = ["www.google.com"] 
result, unans = traceroute(target,maxttl=32) 
print(result,unans)
```
## Output
### CLIENT:
![image](https://github.com/Harevasu/4.Execution_of_NetworkCommends/assets/147985044/8db6ea32-232e-4e4d-9cb8-17fe28905f80)
### SERVER:
![image](https://github.com/Harevasu/4.Execution_of_NetworkCommends/assets/147985044/cc32b8eb-957c-4693-b025-9aa40d34bf97)
### TRACEROUTE COMMAND:
![image](https://github.com/Harevasu/4.Execution_of_NetworkCommends/assets/147985044/a3a76774-1fc5-453b-a0fe-b1bd35d1595a)
## Result
Thus Execution of Network commands Performed 
