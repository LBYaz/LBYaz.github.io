# 搭建笔记终极方法
## 1. 在github上创建仓库

 1.1点击头像，Repositories，New Repository。

 1.2输入仓库名称，__用户名.github.io__（仓库名必须为username.github.io）Github Pages默认域名，Public（公开）Description（可选），Add README。

1.3点击Create repository。

## 2.下载安装 GitHub Desktop

 2.1点击下载[GitHub Desktop](https://desktop.github.com/download/)，安装。

 2.2打开GitHub Desktop，第一次使用选择 Sign in to GitHub.com，跳转到github,com登录页面，输入GitHub账号密码。

 2.3登录成功后，Configure Git，输入GitHub账号密码，确认。
 
 2.4进入Github Desktop初始化工作台，你的仓库里已经显示了 **用户名.github.io**直接使用。（也可以看这几个用：Clone a Repository，Create a New Repository，克隆线上仓库；Create a New Respository，创建本地仓库;Add Local Repository，添加本地仓库）

 2.5直接点击左侧你创建的仓库，选择克隆clone，选择你本地的仓库路径，点击clone(图片显示选择URL)。
 ## 3.创建笔记文件

 3.1打开你本地仓库路径，放入你的Markdown文件（如笔记.md,图片的话建议新建一个文件夹images，把图片放入引用相对路径）。

## 4.提交并推送到Github上

4.1提交变更。回到Github Desktop，左侧会显示新增文件。

4.2在下方Summer里面输入提交说明（如 Add学习笔记.md）,点击Commit to main。

4.3点击Push origin，推送到远程仓库。如果找不到这个按钮，可以使用Repository->Push，推送到远程仓库。你看到Push branch表示首次发布分支与push功能完全一致。

4.4等待几分钟，刷新你的Github Pages域名，就可以看到你的笔记啦！

4.5出现问题：SSL/TLS导致推送失败，可以检查一下网络与代理，关闭VPN代理，切换成手机热点，或者重启电脑重设网络再推送试试。

## 5.验证推送是否成功

5.1查看网页端仓库，刷新，可以看到你的笔记文件。

5.2查看Github Pages是否生效，等待1-5分钟，访问Https://username.github.io，可以看到README.md文件。

5.3在根目录README.md写入跳转代码：

[点击查看笔记]（notes.md）

访问主页时候就会显示这个链接。写完记得提交信息，点击Commit meaaages，提交到远程仓库。

## 6.Github pages主题美化

6.1进入你的仓库，点击settings，点击右上角Add file-create new file，输入_config.yml，(配置主题文件)，输入代码

theme: minima

6.2主题配置后验证步骤：点击仓库顶部Actions选项卡，查看pages-build-deployment的工作流，若显示是绿色就是部署成功。

6.3刷新你的Github Pages域名，可以看到你的博客主题已经变了。





