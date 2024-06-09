Markdown笔记。从第一节课开始<br>
---
# Github基本命令

## 一、GitHub三要素
* 仓库是GitHub项目管理存储的基本单位
* 一个仓库中存储一个项目，一个用户可以拥有多个仓库，一般仓库分为public，private
* 仓库中包含以下内容
  * code、资源存储、代码资源、二进制、项目管理脚本、许可证等；
  * issues，使用时遇到的bug和进行提交
  * README，使用Markdown语言编写，包括工程自述文件、开发进度、版本更新、使用介绍等
  * LISENSE许可证：GPL2.0，3.0;Apahce 2.0,Mit等许可证，给使用者最大使用权限以及最少的限制
* commit提交
  * 程序员在开发时对代码资源的迭代和修改，都可以通过commit的方式进行记录，便于回溯代码
* branch分支
  * 在仓库中包含多个分支，分支才算是代码的第一存储单位，默认的仓库分支为master（本地）
  和main（云端）；不仅可以管理代码存储，还便于多人协作开发。
  示意图如图所示：
 [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240608/2156956e5da0074e238196236507e75a70.png)

## 二、命令操作
### 设备认证
* 设备认证
  * 让网站的账户与设备绑定，后续完成代码的管理，上传下载
    1. git init //创建本地仓库，后续对仓库的操作，都在仓库位置。如下图<br>
    [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/115416cb67672346c393397d03fd142c7f.png)
    2. git config --list  //查看git的配置文件。如下图<br>
       [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/1208825fad7484457b8fe6e641175f777b.png)
    3. git config --global user.email "邮箱号";<br>
       git config --global user.name "昵称" 。如下图<br>
       [https://github.com/daituzi/-/blob/master/README_6_7.md](https://picture.gptkong.com/20240609/121028098d83464be1aafa4d6dd77fe1d3.png)<br>

* 设置密文
  * ssh-keygen -t  rsa -C ''注册邮箱''(用于创建本地密文)SSH远程访问。去对应目录查找密文文件，找.pub文件，复制到网站里，头像，设置，ssh密文，key new，标题随意写，key要写，密码重新写；<br>
  [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/1234813c0448f6434ab447c01cd9cf30f6.png)<br>
  ssh -T git@github.com测试是否成功。如下图：<br>
  [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/12370cd7d3ca6f44ada6e0808044b361e9.png)<br>

* 为仓库起别名，定位目标仓库，方便上传
  * git remote add origin "仓库SSH地址"设置别名 <br>
    git remote remove origin 删除别名；如下图
    [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/1542cd8674063e48af9b6932be7fbc0ca5.png) <br>
### 本地设备与云端仓库的交互逻辑
* 将代码压入git缓冲区：git add code.c
提交到本地仓库：git commit "提交说明"(git commit -m "first upload")
将本地仓库主分支master更新到云端仓库默认分支main(版本更新)：git push origin master(若上传的本地分支与云端默认分支一致，则合并分支；不一致就在云端仓库下创建新分支存储master)
  [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/1546ba00d0d8b5458bbbf076427d67f989.png)
  命令行代码示意图：
  [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/1548bc8e0c82994723ab60abe693b34c21.png)

### 代码更新的依赖关系被破坏
* 如果更新逻辑被破坏，即直接在云端更改代码：一般来说本地内容比云端的新，完成更新替换。但是如果直接修改云端代码，导致本地内容无法再次提交。
  * 解决办法：先拉取git pull 云端内容，与本地内容合并或操作，然后再次push即可
git pull --rebase origin master
git rebase --skip  本地的舍掉，只要云端
git rebase --abort
git rebase --continue
  * 直接更改云端后，本地上传失败，提示用pull
    [https://picture.gptkong.com/20240609/160376777186354a91a97f452c1b8e167a.png](https://picture.gptkong.com/20240609/160376777186354a91a97f452c1b8e167a.png)
  * pull之后，与本地内容合并
    [https://github.com/daituzi/-/blob/master/README_6_7.md](https://picture.gptkong.com/20240609/16056f7ad8f1924e9f96d2c1d6ea79cdeb.png)
  * 合并成功
    [https://github.com/daituzi/-/blob/master/README_6_7.md](https://picture.gptkong.com/20240609/16066a66e7c4204d008087ae04210649cc.png)
  * 代码修改再上传云端
```c
      git add "文件名"
      git commit -m "备注自定义名"
      git push origin master //上传至云端
```
### 下载代码
* 使用命令下载HTTPS地址
git clone 上述地址
下载到了仓库文件夹
删除文件夹也要提交(一套逻辑)

### 分支branch 
* 关于分支的相关命令，创建分支，选择分支，合并分支等
markdown语言
github可以编写readme，文本修饰语言
#### Markdown
* 具体功能查看README.md
* 查看链接：[https://github.com/daituzi/-/blob/master/README.md](https://www.github.com "点击访问")






