# Note1 NewStart #

## 1. Install VS code ##

## 2. Markdown ##

Choose to use VS code to edit markdown files.

Use [Marp for VS Code](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode) as ppt tool.

Use [Markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) as a lint.

Use [vscode-pandoc](https://marketplace.visualstudio.com/items?itemName=DougFinke.vscode-pandoc) to export html, doc and pdf. Note that it's just a plugin, and an extra [Pandoc](https://pan.baidu.com/s/1slawmr7) is still needed.

Start from [a brief instruction of Markdown](https://mazhuang.org/2018/09/06/markdown-intro/ "A brief instruction of Markdown").

## 3. About Workspaces and folders ##

In VS Code, Workspaces and ffolders are different concepts.

Workspaces determine what plugins is loaded - avoid useless loading. Workspaces information can be saved as files. Folders are still folders, contain files.

I choose to save save workspace information on computer and put folders and files on a flash disk.

### Notice: How to add a new workspace ###

File-Close Workspace-File-Save Workspace as.

## 4. Git&Github ##

Start froom [this](https://www.liaoxuefeng.com/wiki/896043488029600/896202815778784).

[A good reference tutorial: The most complete git tutorial](https://blog.csdn.net/yangstarss/article/details/80691775)

So, it's Linus who used two weeks to write a distributed revision control in C, which is Git.

Get github from: [https://github.com/waylau/git-for-win](https://github.com/waylau/git-for-win).
After installation, search git and run Git Bash to have some basical settings:

```git
Username@ComputerName MINGW64 ~
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

Then create a repository and init Git:

```git
Username@ComputerName MINGW64 ~
$ mkdir learngit
$ cd learngit
$ pwd
/c/Users/Lenovo/learngit
$ git init
Initialized empty Git repository in /Users/michael/learngit/.git/
```

Note for windows that if you don't want to make your repository in \c, then right click GitBash-priority window-delet"--ed--home--" in target textbox, and change the path to whatever you want in Starting Position textbox . ([Reference](https://blog.csdn.net/nima1994/article/details/51960101))

Then your GitBash will be like this:

```git
Username@ComputerName MINGW64 YourPath
$
```

And mine as an example:

```git
Lenovo@Lenovo-PC MINGW64 /e
$ mkdir Repository

Lenovo@Lenovo-PC MINGW64 /e
$ cd Repository

Lenovo@Lenovo-PC MINGW64 /e/Repository
$ git init
Initialized empty Git repository in E:/Repository/.git/

Lenovo@Lenovo-PC MINGW64 /e/Repository (master)
$
```

Add a file into repository:

```git
Lenovo@Lenovo-PC MINGW64 /e
$ git add pathOfYourFile

Lenovo@Lenovo-PC MINGW64 /e/Repository (master)
$ git commit -m "Move Note1 into repository"
[master (root-commit) 16ed1d5] Move Note1 into repository
 1 file changed, 35 insertions(+)
 create mode 100644 test/Note1.md
```

## 5. HyperText Markup Language ##

[see this.](https://www.runoob.com/html/html-intro.html)

```HTML
<tag>content</tag>
```

### <!DOCTYPE> ###

```HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>页面标题</title>
</head>
<body>

<h1>我的第一个标题</h1>

<p>我的第一个段落。</p>

</body>
</html>
```

## 6 P.S. Add a repository in Pol.Sta ##

```git

Lenovo@Lenovo-PC MINGW64 /e (master)
$ cd /e/Notes

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git init
Initialized empty Git repository in E:/Notes/.git/

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git add Note1.md

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git commit -m "add Note1.md"
[master (root-commit) d61b563] add Note1.md
 1 file changed, 103 insertions(+)
 create mode 100644 Note1.md

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git push note master
fatal: 'note' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git remote add note git@github.com:PolarisStudio/Deslate_notes.git

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git push note master
To github.com:PolarisStudio/Deslate_notes.git
 ! [rejected]        master -> master (fetch first)
error: failed to push some refs to 'git@github.com:PolarisStudio/Deslate_notes.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$ git push --force note master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 1.56 KiB | 123.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To github.com:PolarisStudio/Deslate_notes.git
 + 9c5d91a...d61b563 master -> master (forced update)

Lenovo@Lenovo-PC MINGW64 /e/Notes (master)
$
```

hahahaha
