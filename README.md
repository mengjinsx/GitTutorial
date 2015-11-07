# Github and Git 图文教程 （未完成）#
图文介绍Windows系统下使用Github账户+msysgit+TortoiseGit进行文件管理的方法。

***声明：作者使用Git的时间很短，对于博大精深的GIT所知甚少，如有任何疏漏之处，希望读者能予以纠正，不胜感激。基于上述原因，此文档会随着作者对GIT的加深了解不断充实内容。***

## 安装 ##

### 安装mysysgit ###

下载地址：[msysgit](http://code.google.com/p/msysgit/downloads/list?q=full+installer+official+git)。下面的截图来自[Git-1.8.1.2-preview20130201.exe](http://code.google.com/p/msysgit/downloads/detail?name=Git-1.8.1.2-preview20130201.exe&can=2&q=full+installer+official+git) 。

![mysysgit-address](./image/mysysgit_download_url.jpg)

安装过程：

0.启动

![mysysgit-0](./image/mysysgit_install0.jpg)

1.默认

![mysysgit-1](./image/mysysgit_install1.jpg)

2.默认

![mysysgit-2](./image/mysysgit_install2.jpg)

3.默认

![mysysgit-3](./image/mysysgit_install3.jpg)

4.默认

![mysysgit-2](./image/mysysgit_install4.jpg)

5.这步骤很重要，选中 **Checkout as-is** 。这样使用 **git clone** 时，git不会擅自改动所获文件的换行符。

![mysysgit-1](./image/mysysgit_install5.jpg)

6.默认

![mysysgit-2](./image/mysysgit_install6.jpg)

7.安装完成。

![mysysgit-1](./image/mysysgit_install7.jpg)

###安装Tortoise###
下载地址：[TortoiseGit](http://code.google.com/p/tortoisegit/wiki/Download?tm=2) 。下面的截图来自[TortoiseGit 1.8.3.0 - 32-bit](http://tortoisegit.googlecode.com/files/TortoiseGit-1.8.3.0-32bit.msi) 。

![Tortoisegit-address](./image/tortoisegit_download_url.jpg)

0.启动

![tortoise-install0](./image/tortoisegit_install0.jpg)

1.默认-Next

![tortoise-install1](./image/tortoisegit_install1.jpg)

2.默认-Next

![tortoise-install2](./image/tortoisegit_install2.jpg)

3.默认-Next

![tortoise-install3](./image/tortoisegit_install3.jpg)

4.默认-Install

![tortoise-install4](./image/tortoisegit_install4.jpg)

5.完成

![tortoise-install5](./image/tortoisegit_install5.jpg)

## 术语 ##

- **repository** 仓库，包含文件历史记录和配置信息的数据库，通常含有多个分支；
- **clone** 仓库的克隆是指仓库的副本拷贝，一个新的克隆包含有原仓库的各种信息；
- **push** 将数据提交到远端仓库；
- **pull** 从远端仓库或本地分支获取数据，然后合并到指定分支；
- **branch** 不同的开发路线；
- **merge** 将数据合并到分支；
- **commit** 将文件更改记录到仓库中；

## 设置 ##

### TortoiseGit 设置 ###

开始->所有程序->TortoiseGit->Settinigs，填入 **Name** 和 **Email** 信息。

这里需要说明，每次通过GIT提交文件时都需要 **Name** & **Email** 信息。这个信息会连同 **Commit Comment** 显示在Github的Commit记录里。

![tortoise-settings](./image/tortoisegit_settings.jpg)

在我们成功将文件上传至Github之后，可以在仓库 **Name** 会在 **Commit** 记录中体现出来。

![git-user-info](./image/git_user_name.jpg)

***为简单起见其他所有的设置项项暂时我们都不做修改，可以在使用中逐渐摸索。***

## 用法 ##

### 配合Github使用 ###

1.登陆github（如没有账号，则需新建一个账号）。点击 **Sign in** 按钮进入登陆页面,填写用户名（或邮箱）与密码后登陆。（用户名与邮箱名不区分大小写，而密码区分大小写）

![github-main-page](./image/github_main_page.jpg)

![github-sign-in-page](./image/github_sign_in_page.jpg)

2.进入 **Account Settings** ，添加 **SSH Key** 。 **SSH Key** 是用户使用SSH工具(本教程里用的是TortoiseGIT里集成的工具)登陆或上传文件至Github时用的密码。

![github-account-settings](./image/github_account_settings.jpg)

![github-ssh-keys](./image/github_ssh_keys.jpg)

3.先从Github上退回到本地。我们需要添加 **SSH Key**， 但是我们现在还没有，所以制作一个先。
开始->所有程序->TortoiseGit->Puttygen 

![tortoisegit-puttygen](./image/tortoisegit_puttygen.jpg)

![tortoisegit-puttygen-start](./image/tortoisegit_puttygen_start.jpg)

点击 **Generate** 按钮开始生成，在指定的区域内移动鼠标加速 **SSH KEY**的产生。

![tortoisegit-puttygen-generate](./image/tortoisegit_puttygen_generate.jpg)

![tortoisegit-puttygen-generating](./image/tortoisegit_puttygen_generating.jpg)

![tortoisegit-puttygen-generated](./image/tortoisegit_puttygen_generated.jpg)

点击 **Save private key** 保存密钥。由于我们没有设置密码，这时会弹出一个窗口问我们是否真的不需要设置 **SSH key** 保护密码。设置密码之后更安全，但在使用的时候每次推送文件都会提示你输入此密码，比较啰嗦，这里可根据个人喜好选择。

![tortoisegit-puttygen-save](./image/tortoisegit_puttygen_save.jpg)

![tortoisegit-puttygen-save-waring](./image/tortoisegit_puttygen_save_warning.jpg)

![tortoisegit-puttygen-save-name](./image/tortoisegit_puttygen_save_name.jpg)

*不需要设置密码的同学可以略过下图*

![tortoisegit-puttygen-set-password](./image/tortoisegit_puttygen_set_password.jpg)

 **暂时不要关闭Puttygen下面还要用到**，如果很不幸你没有看到这句提示。那么也不要紧，重新做一遍吧。

不想重新做一遍的同学可以打开刚才保存的密钥， **File->Open private key** 。如果有同学已经重做，那么恭喜你，你中招了。

4.整理思绪回到Github网站上，相信刚才的页面你还没有关闭，如果关闭了，或者找不到了，那么重新登陆你的Github，右上角点击 **Account Settings** ，然后找到 **SSH Keys**, 点击 **Add SSH Keys** 开始添加。

![github-ssh-keys-add](./image/github_ssh_keys_add.jpg)

![github-ssh-keys-adding](./image/github_ssh_keys_adding0.jpg)

切换到 **Puttygen** 软件，拷贝Public Key 至Github上的 **Add an SSH Key -> Key**窗口。点击 **Add key** ，再之后弹出的密码确认框中输入Github账户密码 点击 **Confirm Password** 完成添加。

![tortoisegit-puttygen-copy-public-key](./image/tortoisegit_puttygen_copy_public_key.jpg)

![github-ssh-keys-adding1](./image/github_ssh_keys_adding1.jpg)

![github-ssh-keys-adding2](./image/github_ssh_keys_adding2.jpg)

![github-ssh-keys-added](./image/github_ssh_keys_added.jpg)

5.现在基本工作已经完成了，下面我们可以开始在Github上建立 **Repository** 并上传文件至Github，开始我们的Github之旅了。

点击右上角的 **Create new repo** 建立新仓库，填入 **Name** (名称)与 **Description** (描述)后，点击 **Create repository** 创建仓库。

![github-create-new-repo0](./image/github_create_new_repo0.jpg)

![github-create-new-repo1](./image/github_create_new_repo1.jpg)

![github-create-new-repo2](./image/github_create_new_repo2.jpg)

创建完仓库后，你的github页面大致如下图所示，红框中有几个可以点击的按钮， **Setup in Windows** , **HTTP** 和 **SSH** 。 

- **Setup in Windows** 不知道怎么使用。

- **HTTP** 非加密连接，只读属性，当获取其他用户的github文件时需要用此种格式的链接。

- **SSH** 加密链接，向自己的仓库中添加上传文件时需要用此种格式的链接，这里我需要使用的链接，即是 *git@github.com:JiapengLi/GitTutorialPractice.git* 。

![github-create-new-repo3](./image/github_create_new_repo3.jpg)

6.现在我们已经成功地在Github上面建立了一个仓库，接下来我们需要使用TortoiseGit工具 **Clone** 刚才建立的仓库，然后添加文件并上传。

- 在Windows资源管理器中单击 **右键**；
- 选择 **Git Clone**项；在 **URL** 项目中添加 **Repository** (仓库)的地址；
- 在 **Directory** 项目中填入目标文件夹(空文件夹或者不存在)；
- 在 **LoadPutty Key** 项目中载入刚刚建立的并保存的Private Key，点击 **OK** 按钮开始 **Clone**；
- **Clone** 结束后点击 **Close** 退出。

![tortoisegit-clone0](./image/tortoisegit_clone0.jpg)

![tortoisegit-clone2](./image/tortoisegit_clone2.jpg)

![tortoisegit-clone3](./image/tortoisegit_clone3.jpg)

![tortoisegit-clone4](./image/tortoisegit_clone4.jpg)

![tortoisegit-clone5](./image/tortoisegit_clone5.jpg)

![tortoisegit-clone6](./image/tortoisegit_clone6.jpg)

7.向Github上传文件。

- 在 **GitTutorial** 文件夹中新建 **README.md** ；
- 编辑 **README.md** ，这里给出了Markdown格式的 **README.md** 样例；
- 另外，为了演示Markdown中添加图片的功能，建立一个 **image** 文件夹(这个名字可以随便取)，并向其添加一些图片

![github-upload0](./image/github_upload0.jpg)

![github-upload1](./image/github_upload1.jpg)

![github-upload3](./image/github_upload3.jpg)

![github-upload4](./image/github_upload4.jpg)

- **GitTutorial**文件夹中右击，选择 **Git Commit->"master"** ；
- 在新弹出的对话框里选择需要上传的文件，填入 **Message** (Message 的内容要对题，描述你此次上传都做了什么)，按OK确认；
- 在新弹出的对话框里单击 **PUSH**按钮上传文件；（在实际开发中，此时可以选择不上传，而在多次Commit之后再上传）
- 在新弹出的对话框里选择 **Local** (本地分支)、 **Ref-Remote** (远程分支)、 **Destination-Remote** (远程目标)，由于我们只有一个分支所以这些项我们都选择默认就可以了，选择 **Autoload Putty Key** ，然后点击OK开始上传；
- 至此我们完成了Github文件的上传。

![tortoise_commit0](./image/tortoisegit_commit0.jpg)

![tortoise_commit1](./image/tortoisegit_commit1.jpg)

![tortoise_commit2](./image/tortoisegit_commit2.jpg)

![tortoise_commit3](./image/tortoisegit_commit3.jpg)

![tortoise_commit4](./image/tortoisegit_commit4.jpg)

完成上传，再次回到Github查看效果。[示例效果](https://github.com/JiapengLi/GitTutorialPractice)

### 本地TortoiseGit使用 ###

(待续)

## TortoiseGit进阶 ##

(待续)

### 多人协作开发 ###
创建Github organization账户
管理Github organization账户
多人合作开发详述：希望在后面可以加上
### TortoiseGit各项的操作所对应的GIT命令 ###

## Tips

### 删除远端分支

	git push origin --delete <branchName>
	
or
	
	git push origin :<branchName>

### 取消文件的版本控制

永久删除:  

    git rm files

从仓库删除，保留本地文件：

    git rm --cached files

### 重命名分支

    git branch -m <oldname> <newname>

    git branch -m <newname> // change current branch name

### 取消最近的一次提交

    git reset --soft HEAD^ (--soft 取消提交保留更改)

    git reset --hard HEAD^ (--hard 取消提交并删除更改)

### 取消文件添加

    git reset HEAD file

### 临时隐藏更改/恢复更改

    git stash save

    git stash pop

### 显示所有未加入版本控制的文件
    git status -vu

### 分支到分支的push
    git push origin local_branch:remote_branch

### 部分历史记录克隆转为全部历史克隆
    git fetch --depth=LargeNumber

### 搜索git log
    git log --all --grep="STRING"

### 创建分支
    git checkout -b new_branch_name commit_code_91f7edc6c1f4440c1
