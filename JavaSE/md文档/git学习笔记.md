1. 生成秘钥指令 ssh-keyen -t rsa - C “[1453058787@qq.com](mailto:1453058787@qq.com) ”
2. 测试连接github ssh -T [git@github.com](mailto:git@github.com)
3.  git merge upstream/main （分支合并）
4.  git clone （克隆代码）
5.  git checkout main （切换分支）
6. git pull —rebase （拉取代码） 
7.  git commit -m "描述信息" (提交代码)
8. git remote，会列出每个远程库的简短名字，在克隆完某个项目后，至少可以看到一个名为origin的远程库，Git默认使用这个名字来标识你所克隆的原始仓库
9. git remote 不带参数，列出已经存在的远程分支
10. git remote -v 列出详细信息，在每一个名字
11.  git config --global --unset http.proxy 关闭代理
12.  git branch -f bugFix "bugFix^" 通过-f 参数可以强制移动分支的位置
13.  git reset local ^ (重置local分支到上一个提交)， dos中需要加引号 git reset “local^”
14.  git cherry-pick 将一个分支上的某个commit 合并到另一个分支，可使用	cherry-pick，注意master上新的commit id于dev上的id并不相同，既只是将dev上的修改拷贝过来，做一个新的提交
15. 尤其注意，重置的操作，首先切换到要重置到的节点没，随后删除重置节点之前的所有的分支
16.  用交互式rebase将3,4,5 压缩成一个分支 （	interactively rebase ……）,可以选择其中一个作为提交的最终节点
17.  先git pull 拉一下，然后再git push 一下，这样push的时候可以避免卡顿



github 账号： 1453058787

​      密码： Lovejavajdk1.8

​      令牌号码： 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





gitee  账号： kaifa996

​       密码： Lovejavajdk1.8



https://github.com/1453058787/Java-NoteBook-Tools.git



———————————————————————————————————

idea 中的git reset中的各个选项的说明，（分支撤回）



1.  **Soft选项：**在选择的回退点之后的所有更改将会保留并被git追踪下来。这就意味着可以在 Version Control 的 Local Changes 面板中查看到它们。
2.  **Mixed模式：**在选择的回退点之后的所有更改将会保留但不会被git追踪下来。
3.  **Hard模式：**在选择的回退点之后的所有更改都会被丢弃。（包括被追踪的和已提交的文件）
4.  **Keep模式：**在选择的回退点之后的所有已提交的更改会被丢弃。但本地修改的会被完整地保存下来。



Soft：在选定提交点之后所做的所有更改都将被暂存（这意味着可以到 Version Control 窗口（Alt+9）的Local Changes 选项卡，以便您可以查看它们，并在必要时稍后提交）。



Mixed：在所选提交之后所做的更改将被保留，但不会暂存以进行提交。



Hard：在所选提交之后所做的所有更改都将被丢弃（已暂存的和已提交的）。



Keep：在选定的提交之后所做的提交更改将被丢弃，但本地更改将保持不变。



——————————————————————————

git merge 和 git rebase的区别

- 首先merge结果能够体现出来时间线，但是rebase会打乱时间线
- 而rebase看起来简洁， 但是merge看起来不太简洁
- 最终结果是都把代码结合起来了，所以具体怎么使用这两个命令还是看项目需要
- 另外，在项目中经常使用git pull来拉取代码，git pull相当于是 git fetch + git merge，如果此时运行git pull -r，也就是git pull -rebase，相当于git fetch + git rebase