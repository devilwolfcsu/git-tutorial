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
