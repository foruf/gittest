<p>工作中有一次不小心提交了不该提交的代码到GIT上，而且在发现之前又提交了几个commit，现在想在GIT服务器上永久删除这个commit，具体步骤记录如下。</p>

<p>假设当前分支为master，当前的commit情况如下，现在需要删除commit_id_2和commit_id_4：</p>

<pre>
commit_id_1
commit_id_2
commit_id_3
commit_id_4
commit_id_5
</pre>

一、创建新的分支，用于reset操作

<pre>
git checkout -b develop
git push orign -u develop
</pre>

二、在新分支develop上，将commit重置到commit_id_4之前的提交

<pre>
git reset --hard <commit_id_5>
</pre>

三、提交新分支，覆盖之前的commit信息

<pre>
git push orign HEAD --force
</pre>

四、按原有的顺序恢复不需要删除的commit，然后提交

<pre>
git cherry-pick commit_id_3
git cherry-pick commit_id_1
git push orign develop
</pre>

五、删除原有的master分支，从develop中checkout一个新分支作为master

<pre>
git push orign --delete master
// 或者 git push orign :master
// 注意：master一般是默认分支，你需要先将默认分支设置为develop才能删除

git checkout -b master
git push orign -u master
// 最后将master重新设置为默认分支
</pre>

<p>操作比较繁琐，但是比较保险，如果有什么好方法，可以分享一下。。</p>

参考：

<pre>
    Delete commits from a branch in Git
    Move the most recent commit(s) to a new branch with Git
</pre>

本文地址：http://xianglong.me/article/permanently-delete-a-commit-from-git/