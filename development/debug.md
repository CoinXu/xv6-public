# Dependents
```
apt install build-essential
```

# Compile
```
cd {xv6 root di}
make CPUS=1 qemu-nox-gdb
```

# Debug
1. By gdb
https://web.archive.org/web/20190308091152/http://zoo.cs.yale.edu:80/classes/cs422/2011/lec/l2-hw

open a new, separate terminal window, change to the same xv6 directory, and type:
```
gdb kernel
```

if display warnings like below:
```bash
$ gdb kernel 
......
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from kernel...
warning: File "/home/coin/Workspace/coder/os/xv6/.gdbinit" auto-loading has been declined by your `auto-load safe-path' set to "$debugdir:$datadir/auto-load".
To enable execution of this file add
        add-auto-load-safe-path /home/coin/Workspace/coder/os/xv6/.gdbinit
line to your configuration file "/home/coin/.gdbinit".
To completely disable this security protection add
        set auto-load safe-path /
line to your configuration file "/home/coin/.gdbinit".
--Type <RET> for more, q to quit, c to continue without paging--Quit
```

create ~/.gdbinit file, and add `add-auto-load-safe-path /your/xv6/root/dir/.gdbinit` 



2. By vscode
add launch.json file for vscode:
```json
{
    "version": "0.2.0",
    "configurations": [
       {
            "type": "gdb",
            "request": "attach",
            "name": "Attach to gdbserver",
            "executable": "${workspaceRoot}/kernel",
            "target": "localhost:26000",
            "remote": true,
            "cwd": "${workspaceRoot}", 
            "gdbpath": "/usr/bin/gdb",
            "autorun": []
        } 
    ]
}
```

open a new terminal window, change to xv6 directory, and type:
```bash
make CPUS=1 qemu-gdb
```
start debug press f5


