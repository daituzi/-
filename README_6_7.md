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
 [本地及云端示意图](https://picture.gptkong.com/20240608/2156956e5da0074e238196236507e75a70.png)

## 二、命令操作
### 设备认证
* 设备认证
  * 让网站的账户与设备绑定，后续完成代码的管理，上传下载
    1. git init //创建本地仓库，后续对仓库的操作，都在仓库位置。如下图<br>
    [创建仓库代码](https://picture.gptkong.com/20240609/115416cb67672346c393397d03fd142c7f.png)
    2. git config --list  //查看git的配置文件。如下图<br>
       [查看配置文件](https://picture.gptkong.com/20240609/1208825fad7484457b8fe6e641175f777b.png)
    3. git config --global user.email "邮箱号";<br>
       git config --global user.name "昵称" 。如下图<br>
       [记录邮箱号和昵称](https://picture.gptkong.com/20240609/121028098d83464be1aafa4d6dd77fe1d3.png)<br>

* 设置密文
  * ssh-keygen -t  rsa -C ''注册邮箱''(用于创建本地密文)SSH远程访问。去对应目录查找密文文件，找.pub文件，复制到网站里，头像，设置，ssh密文，key new，标题随意写，key要写，密码重新写；<br>
  [设置密文](https://picture.gptkong.com/20240609/1234813c0448f6434ab447c01cd9cf30f6.png)<br>
  ssh -T git@github.com测试是否成功。如下图：<br>
  [成功设置密文](https://picture.gptkong.com/20240609/12370cd7d3ca6f44ada6e0808044b361e9.png)<br>

* 为仓库起别名，定位目标仓库，方便上传
  * git remote add origin "仓库SSH地址"设置别名 <br>
    git remote remove origin 删除别名；如下图
    [仓库起别名代码](https://picture.gptkong.com/20240609/1542cd8674063e48af9b6932be7fbc0ca5.png) <br>
### 本地设备与云端仓库的交互逻辑
* 将代码压入git缓冲区：git add code.c
提交到本地仓库：git commit "提交说明"(git commit -m "first upload")
将本地仓库主分支master更新到云端仓库默认分支main(版本更新)：git push origin master(若上传的本地分支与云端默认分支一致，则合并分支；不一致就在云端仓库下创建新分支存储master)
  [交互逻辑示意图](https://picture.gptkong.com/20240609/1546ba00d0d8b5458bbbf076427d67f989.png)
  命令行代码示意图：
  [命令行代码示意图](https://picture.gptkong.com/20240609/1548bc8e0c82994723ab60abe693b34c21.png)

### 代码更新的依赖关系被破坏
* 如果更新逻辑被破坏，即直接在云端更改代码：一般来说本地内容比云端的新，完成更新替换。但是如果直接修改云端代码，导致本地内容无法再次提交。
  * 解决办法：先拉取git pull 云端内容，与本地内容合并或操作，然后再次push即可
git pull --rebase origin master
git rebase --skip  本地的舍掉，只要云端
git rebase --abort
git rebase --continue
  * 直接更改云端后，本地上传失败，提示用pull
    [更改云端提示](https://picture.gptkong.com/20240609/160376777186354a91a97f452c1b8e167a.png)
  * pull之后，与本地内容合并
    [代码示意图](https://picture.gptkong.com/20240609/16056f7ad8f1924e9f96d2c1d6ea79cdeb.png)
  * 合并成功
    [示意图](https://picture.gptkong.com/20240609/16066a66e7c4204d008087ae04210649cc.png)
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
* 查看链接：[README.md](https://github.com/daituzi/-/blob/master/README.md "点击访问")

## 正则表达式
### 定义：正则表达式技术：经典的数据处理技术，可以实现数据查询匹配和数据清洗等
### 适用于模糊查询
* 为什么要使用模糊查询？
  ** 查询文件中的某个单词：使用strstr、strcmp函数可以对简易的字符串进行查询，但对于大数据量不合适，由于是按照单个字符的ASCII码值匹配的，所以匹配效率低，开销大。同时无法模糊查询
  ** 正则技术采用贪心算法完成数据模式匹配，匹配的效率更高。而且正则技术在各个系统和语言中都有实现，便于跨平台处理。
* 什么是贪心算法？
  ** 贪心算法：每一步都选择当前最优解（但是整体可能不是最优）
* 正则语句：是由若干特殊符号(表达式)构成的长字符串，这个字符串用于描述数据的规则，后续对数据进行模式匹配。
  ** 规范存储数据：如果存储的数据格式清晰明确，那么使用正则匹配提取数据比较方便，否则正则不一定适用。
  ** 存放HTML标签存储形式：<name>张三</name> <sex>男</sex>等；
  ** 数据存储需要一定的规则和格式，便于后续数据的使用，不要直接无格式字节流存储(如直接存放内容信息，张三，男)，这样在大数据量下，难以查询需要的内容
### 正则技术匹配流程：grep '正则表达式' 数据源
### 正则原字符
* 1、转义符\：取消本意或赋予某个含义
* 2、星号* ：向前参照，表示该表达式出现零次或多次：如grep 'a*' 源文件 ，则显示包含a(高亮)和没有a的；aa*，则只有a开头的才有(a表示a出现1次，a*表示a出现0次或多次)
  ![a*](https://picture.gptkong.com/20240613/1155043978ec434b92bde0c5342b383ce4.png)
  ** 正则表达式为a\+时，表示该表达式出现一次或多次
  ![a\+](https://picture.gptkong.com/20240613/132191615abb6348248200245aa29e68cb.png)
  ** 正则表达式为a时，是以单个a做查询的，效率低，查询结果同上，有a的才会输出
  ![a](https://picture.gptkong.com/20240613/1322f872c7cf2949219f22aefeca14851e.png)
* 3、^a ：向后一个表达式作为参照，a为行首
  ![^a](https://picture.gptkong.com/20240613/1323375aef75704cc7a6a77e2c823b4018.png)
* 4、a$ ：向前一个表达式作为参照，a为行尾
  ![a$](https://picture.gptkong.com/20240613/132357ad2ea7824857955f3e0a4ff11d4c.png)
* 5、点. :表示任意的一个字符出现0次或多次
  ![.](https://picture.gptkong.com/20240613/1324034552b68b4900a3fa6a0d7adbbdf2.png)
* 6、方括号[]：表达式集合，集合出现时表示任意一个表达式
  !["[]"](https://picture.gptkong.com/20240613/1324f02455779c4bef82d84fb736c4d932.png)
  ** [ab]xxx，可以匹配到axxx和bxxx
  ** 常用写法：
  1. 小写字母集合[a-z]
  2. 大写字母集合[A-Z]
  3. 数字集合[0-9]
  4. 有效字符集合[a-zA-Z0-9]
  5. [^a-z]，集合取非
* 7、grep -v '^$' 源文件>新文件：将源文件中的空行去掉并输入到新文件里；该表达式是匹配空行
  ![匹配空行](https://picture.gptkong.com/20240613/132549e1b209db45138d6b914d1da6f524.png)
* 8、大括号\{\}，需要转义符：大括号里是指定频率/出现次数
  ![指定频率](https://picture.gptkong.com/20240613/1326116f8f53354c86b10909e0b30b0303.png)
  1. a{n}，以前一个表达式为参照，该表达式连续出现的频率
  2. a{n,},最小出现n次，最大不设限制
  3. a{n,m}最小出现n次，最大出现m次
* 9、实现词匹配(内容)：\（某某\）\+   表示该词出现一次或多次
  ** 例题：匹配电话号码：规则为：全为数字；十一位；首位为1；第二位为3-9，后九位为0-9；
  ![电话号码](https://picture.gptkong.com/20240613/13278ae1cc837c423d9348cdddb85d97f0.png)
* 10、逻辑或丨：字符集合中无需转义，其他位置使用需要转义：注意例子，邮箱的.com和.cn是用()括起来的，否则会变成前面所有，逻辑或上后面的，就会显示白色
  ![邮箱](https://picture.gptkong.com/20240613/13295c7ec2baf04a67a2b7555154890072.png)
