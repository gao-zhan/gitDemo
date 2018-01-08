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
8)git diff  查看修改内容
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

   

