# gittest
vscode git test

# vscode添加git
<a href="http://www.cnblogs.com/xuanhun/p/6019038.html?utm_source=tuicool&utm_medium=referral">http://www.cnblogs.com/xuanhun/p/6019038.html?utm_source=tuicool&utm_medium=referral</a>

<p>先本地创建git，然后在远程创建项目，之后运行如下命令</p>
<pre>
git remote add origin 远程地址 //添加远程地址
git pull origin master //把远程文件同步到本地
</pre>
<p>然后配置用户名和邮箱，然后就可以发布了。</p>

# git 用远程覆盖本地
<p>本地有修改和提交，如何强制用远程的库更新更新。我尝试过用Git pull -f，总是提示 You have not concluded your merge. (MERGE_HEAD exists)。</p>

<p>我需要放弃本地的修改，用远程的库的内容就可以，应该如何做？傻傻地办法就是用心的目录重新clone一个，正确的做法是什么？</p>

<p>正确的做法应该是：</p>

<pre>
git fetch --all
git reset --hard origin/master
git fetch 只是下载远程的库的内容，不做任何的合并git reset 把HEAD指向刚刚下载的最新的版本

git fetch origin master可以拉取远程master分支所有的内容吗？可以的哦~
</pre>

<p>参考链接：</p>

<a href="http://stackoverflow.com/questions/1125968/force-git-to-overwrite-local-files-on-pull">http://stackoverflow.com/questions/1125968/force-git-to-overwrite-local-files-on-pull</a>

# 查看所有分支
<pre>git branch -a</pre>

# 删除本地分支
<pre>git branch -D <branchName></pre>

# 删除远程分支
<pre>git push origin --delete <branchName></pre>

# 设置用户名
<pre>git config user.name <userName></pre>

# 设置邮箱
<pre>git config user.email <email></pre>

# 回到某个commit_id，并改变远程数据
<pre>
git reset --hard <commit_id>
git push origin HEAD --force
</pre>