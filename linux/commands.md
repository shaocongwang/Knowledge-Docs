# Linux 的实操命令集

## linux 系统相关

### linux 系统线程和进程
    $ ulimit -s # 线程多大
    $ ulimit -u # 每个用户最多多少进程和线程
    $ systemctl show user-$UID.slice -p TasksMax # ststemd 给你的任务上限
    $ cat /proc/sys/kernel/threads-max #整台机器的线程上限
    $ ps -eLf | wc -l #现在已经有多少线程
    

### for temp git test



