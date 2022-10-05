## docker 底层技术
* cgroup （资源控制，CPU，内存）
* namespace （进程隔离）
* rootfs (aufs)
* * 联合文件系统，删除使用whiteout技术，在读写层新增 .wh前缀文件，以形成当前文件被删除的假像
* * 新增文件，采用Copy-on-write技术，在读写层新增文件
```
sudo mount -t aufs -o dirs=./fruits:./vegetables none ./mnt
```


## docker 四种网络模式
docker network ls
* host
* container
* none
* bridge
https://www.jianshu.com/p/22a7032bb7bd

--link 是单向网络模式，所以现在使用 network方式
https://www.cnblogs.com/windyet/articles/10139739.html


## CMD / Entrypoint


## docker-entrypoint.sh
`很多官方镜像entrypoint 都是 docker-entrypoint.sh 脚本，实际上是通过shell执行预处理逻辑，然后：
exec "$@"
把启动容器入口正式交给使用者`