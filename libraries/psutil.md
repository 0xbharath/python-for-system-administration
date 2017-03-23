
# psutil

[psutil documentation](https://pythonhosted.org/psutil/)


- `psutil` (python system and process utilities) is a *cross-platform* library for retrieving information on running processes and system utilization (CPU, memory, disks, network, sensors) in Python.

- `psutil` is useful mainly for system monitoring, profiling, limiting process resources and the management of running processes.

- `psutil` implements many functionalities offered by command line tools such as: `ps`, `top`, `lsof`, `netstat`, `ifconfig`, `who`, `df`, `kill`, `free`, `nice`, `ionice`, `iostat`, `iotop`, `uptime`, `pidof`, `tty`, `taskset`, `pmap`.

## Installing psutil

- Easiest way to install `psutil` is via `pip`

```
$ pip install psutil
```

## psutil usage

#### List of logged in users

- command `w` on many Unix-like operating systems provides a quick summary of every user logged into a computer, what each user is currently doing.
- `psutil` provides nearly the same output through `users` method.

```
>>> pprint(psutil.users())
[suser(name='bob', terminal='tty9', host='localhost', started=1488969344.0),
 suser(name='bob', terminal='pts/0', host='localhost', started=1488969472.0),
 suser(name='ecrts', terminal='pts/2', host='localhost', started=1488987648.0),
```

#### process details

- Print details of all the running processes

```
>>> for proc in psutil.process_iter():
...     print proc
... 
psutil.Process(pid=1, name='systemd')
psutil.Process(pid=2, name='kthreadd')
psutil.Process(pid=3, name='ksoftirqd/0')
... snipped ...
psutil.Process(pid=27362, name='chrome')
psutil.Process(pid=29322, name='dockerd')
```

- print name of all the running processes

```
>>> for proc in psutil.process_iter():
...     print proc.name()
systemd
ksmd
... snipped ...
khugepaged
crypto
chrome
dockerd
```

- kill a process by name

```
import psutil
 
PROCNAME = 'chrome'
 
def kill_chrome():
    for proc in psutil.process_iter():
        if proc.name == PROCNAME:
            proc.kill()
```




#### network information

- List of network interfaces

```
>>> [p for p in psutil.net_if_stats()]
['docker0', 'vmnet1', 'wlp2s0', 'lo', 'vmnet8', 'enp1s0']
```


```
>>> pprint(psutil.net_if_stats())
{'docker0': snicstats(isup=True, duplex=0, speed=0, mtu=1500),
 'enp1s0': snicstats(isup=True, duplex=1, speed=10, mtu=1500),
 'lo': snicstats(isup=True, duplex=0, speed=0, mtu=65536),
 'vmnet8': snicstats(isup=True, duplex=0, speed=0, mtu=1500),
 'wlp2s0': snicstats(isup=True, duplex=0, speed=0, mtu=1500)}
```


