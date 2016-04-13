# gitHub仓库初始化

[TOC]

## 命令行创建新仓库

	echo "# git-tutorial" >> README.md
	git init
	git add README.md
	git commit -m "first commit"
	git remote add origin git@github.com:<github-username>/<new-repository-name>.git
	git push -u origin master

