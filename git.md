## 基本操作
```git
git config --global user.name "Name"
git config --global user.email "email@qq.com"
pwd					#当前目录
cd
mkdir					#新建文件夹
```

```git
git init
git add 1.txt
git add 2.txt 3.txt			#添加多个文件
git commit -m '此版本说明'
```

## Git版本管理
```git
git status				#查询Git当前状态，常用
git diff 1.txt				#查询代码修改区别
git log					#查询git历史，显示太多时按q退出
git reflog				#查询历史版本号
```

版本回退。
```git
git reset --hard HEAD^
git reset --hard HEAD^^			#回退到上上次
git reset --hard HEAD~77		#回退第前77次修改
git reset --hard HEAD 8yfhY45		#回退到具体的版本号
git checkout -- 1.txt			#撤销此次修改
rm 1.txt				#删除文件,checkout可恢复
```
## 连接GitHub远程仓库
```git
git remote add origin https://github.com/Aeron9000/testgit
git push -u origin master			#本地仓库推送到远程仓库，第一次带-u参数关联本地远程
git push origin master				#本地推送到远程仓库，推送主分支master
git clone https://github.com/Aeron9000/testgit2	#远程仓库克隆到本地
```

## Git分支管理
```git
git branch chs   			#创建chs分支
git checkout -b chs			#创建并切换到chs分支，只切换不带-b参数
git branch				#查看当前分支
git merge chs				#在master主分支下与chs合并
git branch -d chs			#删除chs分支
```
如果分支合并产生冲突，可git status查询、merge、再add + commit，push之后即可delete分支。

远程协作管理。
```git
git merge –no-ff  -m “注释” bno		#不用Fast Forword模式合并
git stash 				#隐藏该分支
git stash list
git stash pop				#恢复该分支并删除stash list中的
git remote				#查询远程库
git remote -v 		 		#查询远程库详细信息
```

多人协作。
```git
git push origin chs			#chs分支推送到远程库
git checkout -b chs origin/chs		#远程oorigin的chs分支到本地
git pull				#最新的提交从origin/chs抓下，在本地合并解决冲突

个人博客：https://blog.csdn.net/qm9090/article/details/90673007
