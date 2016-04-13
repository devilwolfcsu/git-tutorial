# 生成SSH key

[TOC]

SSH keys提供一种不涉及密码来识别可信计算机的方式。跟随下面的文章内容你可以生成SSH key并且将公钥添加到github账户中。我们建议你定期检查你的SSH keys列表，并且删除不再使用的。

## 一、 检查是否已经存在SSH keys

生成SSH key之前，首先你应该检查你是否已经存在了一个SSH key:

1. 打开 Git Bash；
2. 输入 ls -al ~/.ssh来检查SSH key是否已经存在；

		ls -al ~/.ssh
        # 将列出.ssh文件夹下的所有存在的文件
3. 检查目录里面是否已经有一个SSH公钥。

公钥一般情况下如下所示：

	id_dsa.pub
    id_ecdsa.pub
    id_ed25519.pub
    id_rsa.pub

如果在文件夹下没有公钥或者你不想使用已经有的公钥，请继续向下看；
如果你想使用已经存在的公钥应用到github上，请跳到//TODO

## 二、生成新的SSH key并且添加到ssh-agent

### 2.1 生成新的SSH key

1. 打开git bash；
2. 执行如下命令，替换为自己的email地址：

		ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
3. 默认情况下（看到如下提示）直接回车；

		Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
4. 输入安全密码，生成SSH key(可为空)：

		Enter passphrase (empty for no passphrase): [Type a passphrase]
		Enter same passphrase again: [Type passphrase again]

### 2.2 将SSH key 添加到ssh-agent

1. 确定ssh-agent是可用的：

* 如果使用git bash ，执行如下命令打开ssh-agent

		# start the ssh-agent in the background
		eval "$(ssh-agent -s)"
		Agent pid 59566
* 如果是别的终端，执行如下命令：

		# start the ssh-agent in the background
		eval $(ssh-agent -s)
		Agent pid 59566

2. 将SSH key添加到ssh-agent,其中`id_rsa`为对应SSH key文件名；

		$ssh-add ~/.ssh/id_rsa

## 3. 将SSH key天骄到GitHub账户

1. 使用如下命令将SSH key拷贝到剪切板（文件名为生成的`*.pub文件`）

		$ clip < ~/.ssh/id_rsa.pub
		# Copies the contents of the id_rsa.pub file to your clipboard
2. 在右上角点击用户头像，选择*settings*;
3. 左侧选择 *SSH and GPG keys*；
4. 点击 *New SSH key*；
5. *Title*处为本SSH key描述，可随意起名，方便自己辨认；
6. 将key粘贴到*Key*处；
7. 点击*Add SSH key*
8. 输入GitHub 账户的密码确认该操作。

## 4. 测试SSH连接

1. 打开Git Bash；
2. 输入如下命令：

		ssh -T git@github.com
		# Attempts to ssh to GitHub
有安全提示直接输入yes,回车，你将看到如下信息：

		Hi username! You've successfully authenticated, but GitHub does not
		provide shell access.