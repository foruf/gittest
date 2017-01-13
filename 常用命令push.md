详细的命令使用说明，请参考<a href="http://www.yiibai.com/git/home.html">点击打开链接</a>

<p>git push命令用于将本地分支的更新，推送到远程主机。它的格式与git pull命令相仿。</p>

<pre>$ git push <远程主机名> <本地分支名>:<远程分支名></pre>
<p>注意，分支推送顺序的写法是<来源地>:<目的地>，所以git pull是<远程分支>:<本地分支>，而git push是<本地分支>:<远程分支>。</p>

<p>如果省略远程分支名，则表示将本地分支推送与之存在”追踪关系”的远程分支(通常两者同名)，如果该远程分支不存在，则会被新建。</p>

<pre>$ git push origin master</pre>
<p>上面命令表示，将本地的master分支推送到origin主机的master分支。如果后者不存在，则会被新建。</p>

<p>如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。</p>

<pre>$ git push origin :master</pre>
<p> 等同于</p>
<pre>$ git push origin --delete master</pre>
<p>上面命令表示删除origin主机的master分支。</p>

<p>如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。</p>

<pre>$ git push origin</pre>
<p>上面命令表示，将当前分支推送到origin主机的对应分支。</p>

<p>如果当前分支只有一个追踪分支，那么主机名都可以省略。</p>

<pre>$ git push</pre>
<p>如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push。</p>

<pre>$ git push -u origin master</pre>
<p>上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。</p>

<p>不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。如果要修改这个设置，可以采用git config命令。</p>

<pre>$ git config --global push.default matching</pre>
<p> 或者</p>
<pre>$ git config --global push.default simple</pre>
<p>还有一种情况，就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要使用–all选项。</p>

<pre>$ git push --all origin</pre>
<p>上面命令表示，将所有本地分支都推送到origin主机。</p>

<p>如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做git pull合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用–force选项。</p>


<pre>$ git push --force origin</pre>
<p>上面命令使用–force选项，结果导致在远程主机产生一个”非直进式”的合并(non-fast-forward merge)。除非你很确定要这样做，否则应该尽量避免使用–force选项。</p>

<p>最后，git push不会推送标签(tag)，除非使用–tags选项。</p>

<pre>$ git push origin --tags</pre>

<p>有时候当远程xxx分支被删掉了后，用git branch -a 你还可以看到本地还有remote/origin/xxx这个分支，那么你可以使用git fetch -p 这个命令可以帮你同步最新的远程分支，并删掉本地被删了的远程分支</p>