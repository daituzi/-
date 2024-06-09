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
* 设备认证
  * 让网站的账户与设备绑定，后续完成代码的管理，上传下载
    1. git init //创建本地仓库，后续对仓库的操作，都在仓库位置。如下图<br>
    [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/115416cb67672346c393397d03fd142c7f.png)
    2. git config --list  //查看git的配置文件。如下图<br>
       [https://github.com/daituzi/-/blob/master/README\_6\_7.md](https://picture.gptkong.com/20240609/1208825fad7484457b8fe6e641175f777b.png)
    3. git config --global user.email "邮箱号"
    4. git config --global user.name "昵称" 。如下图<br>
       [https://github.com/daituzi/-/blob/master/README_6_7.md](https://picture.gptkong.com/20240609/121028098d83464be1aafa4d6dd77fe1d3.png)

