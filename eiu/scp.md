---
title: scp
category: bash
layout: 2017/sheet
---



### scp命令需要指定端口时要紧跟在scp后

　　问题来源：我本地是Ubuntu操作系统，有时需要更新一些文件到服务器。但是，为了安全起见我们都是将服务器的sshd端口修改的，通常不使用默认的22号端口。

　　　　如果我们使用scp命令时：scp upload_file username@server时就会遇到　　

　　　　　　ssh: connect to host my_server port 22: Connection refused

　　　　注意：在需要指定端口时要使用-P(大写的P)，而且要紧跟在scp之后：scp -P 12349 upload_file username@server（正确）

　　　　-P 如果放在远程主机之后会遇到这样的错误：scp upload_file username@server -P 12349（错误）

　　　　　　12349: No such file or directory

　　　　　在使用时请将12349换成自己服务器对应的端口！

```
D:\vag-files\ubuntu16
λ  scp .\lcnx_eiss-with-data.sql -P 2222 -i D:/vag-files/ubuntu16/.vagrant/machines/default/virtualbox/private_key vagrant@127.0.0.1:/home/vagrant/
ssh: connect to host 127.0.0.1 port 22: Connection refused
lost connection
D:\vag-files\ubuntu16
λ  scp -P 2222 -i D:/vag-files/ubuntu16/.vagrant/machines/default/virtualbox/private_key .\lcnx_eiss-with-data.sql vagrant@127.0.0.1:/home/vagrant/
lcnx_eiss-with-data.sql                                                                                                                                                                                     100% 8394KB   8.2MB/s   00:00
D:\vag-files\ubuntu16
```




## ref
- https://www.cnblogs.com/jixingke/p/6213074.html
 
