���ͣ�https://blog.csdn.net/qm9090/article/details/90673007

## ��������
```git
git config --global user.name "Name"
git config --global user.email "email@qq.com"
pwd					#��ǰĿ¼
cd
mkdir					#�½��ļ���
```

```git
git init
git add 1.txt
git add 2.txt 3.txt			#��Ӷ���ļ�
git commit -m '�˰汾˵��'
```

## Git�汾����
```git
git status				#��ѯGit��ǰ״̬������
git diff 1.txt				#��ѯ�����޸�����
git log					#��ѯgit��ʷ����ʾ̫��ʱ��q�˳�
git reflog				#��ѯ��ʷ�汾��
```

�汾���ˡ�
```git
git reset --hard HEAD^
git reset --hard HEAD^^			#���˵����ϴ�
git reset --hard HEAD~77		#���˵�ǰ77���޸�
git reset --hard HEAD 8yfhY45		#���˵�����İ汾��
git checkout -- 1.txt			#�����˴��޸�
rm 1.txt				#ɾ���ļ�,checkout�ɻָ�
```
## ����GitHubԶ�ֿ̲�
```git
git remote add origin https://github.com/Aeron9000/testgit
git push -u origin master			#���زֿ����͵�Զ�ֿ̲⣬��һ�δ�-u������������Զ��
git push origin master				#�������͵�Զ�ֿ̲⣬��������֧master
git clone https://github.com/Aeron9000/testgit2	#Զ�ֿ̲��¡������
```

## Git��֧����
```git
git branch chs   			#����chs��֧
git checkout -b chs			#�������л���chs��֧��ֻ�л�����-b����
git branch				#�鿴��ǰ��֧
git merge chs				#��master����֧����chs�ϲ�
git branch -d chs			#ɾ��chs��֧
```
�����֧�ϲ�������ͻ����git status��ѯ��merge����add + commit��push֮�󼴿�delete��֧��

Զ��Э������
```git
git merge �Cno-ff  -m ��ע�͡� bno		#����Fast Forwordģʽ�ϲ�
git stash 				#���ظ÷�֧
git stash list
git stash pop				#�ָ��÷�֧��ɾ��stash list�е�
git remote				#��ѯԶ�̿�
git remote -v 		 		#��ѯԶ�̿���ϸ��Ϣ
```

����Э����
```git
git push origin chs			#chs��֧���͵�Զ�̿�
git checkout -b chs origin/chs		#Զ��oorigin��chs��֧������
git pull				#���µ��ύ��origin/chsץ�£��ڱ��غϲ������ͻ