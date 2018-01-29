# 1:检查当前用户是不是根用户的方法
```

[root@test ~]# if [ $UID == $EUID ];then echo OK;fi
OK
[root@test ~]# if [ $UID == 0 ];then echo OK;fi
OK
[root@test ~]# echo $UID
0
[root@test ~]# su - peter
[peter@test ~]$ echo $UID
1000
[peter@test ~]$ exit
logout
[root@test ~]# if [ $UID -eq 0 ];then echo OK;fi
OK

```
# 2: 使用或操作符来显示提供提示信息(或操作是: || )
```

dir='/var/log/confluent/console'
cd $dir || {
        echo -e "problem when enter directory $dir"
}
```
### 执行结果:
```
[roott@test ~]# bash or_operatior.sh
or_operatior.sh: line 9: cd: /var/log/confluent/console: No such file or directory
problem when enter directory /var/log/confluent/console
[root@test ~]#
[root@test ~]# mkdir /var/log/confluent/console -p
[root@test ~]# bash or_operatior.sh


```

# 3: 与操作符的应用示例 （与操作符是: && ） 
```

```

# : 
```
```
