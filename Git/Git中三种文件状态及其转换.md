新建README.txt文件，接着，使用“git status”查看文件状态

Git友好的标示出README.txt为“Untracked files”，并且提示使用“git add <file>...”的命令将文件包含到待提交清单中。按照提示，使用“git add README.txt”命令，然后，使用“git status”查看文件状态

文件README.txt状态变成了“Changes to be committed”，也就是说README.txt在暂存区域生成了快照，等待被提交。正如Git所提示的那样，通过“**git rm --cached README.txt**”命令，可以将文件状态还原为未暂存状态，即回到“Untracked files”文件状态。现在，README.txt已经可以被提交到git目录中了，但是暂时不提交。打开README.txt，向其中加些内容，保存之后，用“git status”查看

可以看到，除了之前的“Changes to be committed”状态，现在又多了一条“Changes not staged for commit”状态，表明文件已经修改，但是还没有放入暂存区域，也就是没生成快照。如果现在进行commit操作，只是将修改之前的文件快照提交到了git目录，一定记住：只有暂存区域的文件（即：文件状态为“Changes to be committed”）才会被提交。正如提示，通过“git add README.txt”命令将已修改文件更新到暂存区域中，如果想撤销修改，可以使用“**git checkout -- README.txt**”命令。

### 放弃修改

不知道大家有没有注意到：在上述`git commit`结果中有这样一句
 **(use "git checkout -- <file>..." to discard changes in working directory)**
 即：**git checkout --<file>可以丢弃工作区的修改**。

命令`git checkout -- README.MD`就是，把README.MD在工作区的修改全部撤销，这里有两种情况：

- 自修改后还没有被放到暂存区，撤销修改就回到和版本库一模一样的状态；
- 已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，**让这个文件回到最近一次git commit或git add时的状态**。
 `git checkout -- <file>`命令中的`--`很重要，没有就变成了“切换分支”的命令。

此时我们查看文件的内容，果然回到了修改前的内容。

### 文件四种状态

#### untracked

未跟踪，此文件在文件夹中，但并没有加入git库，不参与版本控制。 通过”git add”,”git commit”可将它置入跟踪库。

#### unmodify

文件已经库中，未修改，即版本库中的文件快照内容与文件夹中完全一致。这种类型的文件有两个去处，如果它被修改，而成为modified。如果使用”git rm”移出版本库，则成为untracked文件。

#### modified

文件已修改，仅仅是修改，并没有进行其它操作。这个文件也有两个去处，通过”git add”可进入暂存(staged)状态，使用”git checkout”则丢弃修改，返因到unmodify状态。这个checkout很好理解，就是取出库中文件，覆盖当前文件吧。

#### staged

暂存状态。执得”git commit”则将修改同步到库中，这时库中的文件与本地文件又一致了，于是文件是unmodify状态。执行”git reset HEAD filenam”取消暂存，文件状态变为modified。