# 1： 登录github
# 2:  创建一个仓库
# 3:  创建本地的仓库
```
[root@test ~]# cd /data3
[root@test data3]# mkdir bash_shell
[root@test data3]# cd bash_shell/
[root@test bash_shell]# git init

```
# 4： 关联远程仓库
```
[root@test bash_shell]# git remote add bash_shell https://github.com/824380210/bash_shell
```
# 5: 给本地仓库添加文件
```
 git add 
 git commit -m 
```
# 6: 同步到远程仓库中
```
[root@test bash_shell]# git push -u bash_shell
To git@github.com:824380210/bash_shell.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:824380210/bash_shell.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
# 7 如果碰上上面问题，说明是两个库有差异（第一次同步），需要 勾选强制覆盖已有的分支（可能会丢失改动）
```
[root@test bash_shell]# git push -u bash_shell -f
Counting objects: 3, done.
Delta compression using up to 40 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 501 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To git@github.com:824380210/bash_shell.git
 + 5188f48...cf9df5d master -> master (forced update)
Branch master set up to track remote branch master from bash_shell.

```

