## git讲解 ##

1）git:分布式版本控制系统，内容管理系统(CMS),工作管理系统。
2）Git 与 SVN 区别点：
  1、GIT是分布式的，SVN不是。
  2、GIT把内容按元数据方式存储，而SVN是按文件：所有的资源控制系统都是把文件的元信息隐藏在一个类似.svn,.cvs等的文件夹里。
  3、GIT分支和SVN的分支不同：分支在SVN中一点不特别，就是版本库中的另外的一个目录。
  4、GIT没有一个全局的版本号，而SVN有：目前为止这是跟SVN相比GIT缺少的最大的一个特征。
  5、GIT的内容完整性要优于SVN：GIT的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。

---解析：SHA-1(安全散列算法1)：和MD5一样，统称为哈希算法。把任意长度的数据计算成固定长度的数据。
                 MD5返回值是128bit，按十六进制表示的话是32位十六进制的数。
                 SHA-1返回值是160bit，按十六进制表示的话是40位十六进制的数。
               MD5：http://md5-hash-online.waraxe.us/
             SHA-1：http://sha1-hash-online.waraxe.us/
3)git安装：
4)git init 把这个目录变成Git可以管理的仓库
           创建完之后，多出来一个 .git目录 :该目录包含了资源的所有元数据,其他的项目目录保持不变(SVN会在每个子目录生成 .svn 目录，Git 只在仓库的根目录生成 .git 目录)
            ls -ah 查看该目录  *切记不要乱改该目录文件，否则容易把仓库破坏

5)git add
6)git commit -m '说明'


7)git status  查看文件状态 是否被修改过


8)git diff readme.md 查看修改内容
      git diff HEAD -- readme.md


9)git log 查看提交日志 从最近到最远显示
       添加参数--pretty=oneline 精简显示信息, 即：git log --pretty=oneline


10)git reset --hard HEAD^  回退到上一个版本
                    HEAD 指向当前版本
                    HEAD^^ 上上个版本
                    HEAD~100 往上100个版本


11)回退之后想回来该怎么办？
   git reset --hard 版本号   (版本号写前几位就ok)
   找不到版本号该怎么办?
   git reflog  (每一次命令的记录)


12)git checkout -- readme.md 撤销工作区的修改
   git reset HEAD readme.md   把暂存区的修改撤销掉

13)删除文件:
        工作区删除  rm readme.md
        工作区删除不代表版本库删除：用git rm readme.md 删除版本库的该文件
                                git commit -m '删除该文件'
        如果工作区删错文件的话：撤销工作区操作：命令见（12）
    注意：git rm 删除一个文件，如果该文件已经被提交到版本库，不用担心被误删，但是只能恢复到最新版本，你会丢失最近一次提交后你修改的内容.

14）远程仓库
        本地电脑生成SSH Key ：ssh-keygen -t rsa -C "youremail@example.com"
        git remote add origin git@server-name:path/repo-name.git；
        git push -u origin master；
        操作演示该步骤
        第一次clone或者push的时候，会有一个警告，需要验证

15)git checkout -b 分支名      --新切分支并且切换到当前分支


16)git checkout  分支名        --切换分支

17)git branch                 --查看当前分支

18)git merge 分支名            --合并分支

            注意:合并分支时，加上--no-ff参数就可以用普通模式合并，合并后的历史有分支，能看出来曾经做过合并，而fast forward合并,删除分支后，会丢掉分支信息,就看不出来曾经做过合并。
                git merge --no-ff -m "xxx" 分支名

19)git branch -d 分支名        --删除分支

20)git log --graph            --查看分支合并图

21)git stash  储藏分支

22）git stash list  查看储藏的分支列表

23)git stash apply 恢复储藏分支,但是stash内容没删除    git stash apply stash@{0} 恢复指定的stash
   git stash drop 删除stash；

   快捷方法：git stash pop 恢复的同时进行删除stash

24)git branch -d 分支名      --删除分支
   git branch -D 分支名      --强行删除