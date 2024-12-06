# 使用命令行方式批量删除本地分支（基于特定前缀或条件）
如果你想删除所有以某个前缀开头的本地分支，可以使用git branch命令结合grep和xargs来实现。例如，假设你想删除所有以feature -开头的分支。
首先，使用git branch | grep "feature -"命令来列出所有以feature -开头的分支。这个命令中，git branch用于列出所有本地分支，grep "feature -"用于筛选出包含feature -的分支名称。
然后，将上述命令的输出作为xargs命令的输入，用于执行git branch -D（强制删除分支）操作。完整的命令是git branch | grep "feature -" | xargs git branch -D。
这里的-D参数表示强制删除分支，即使分支包含未合并的更改也会删除。如果希望在分支已经合并到其他分支的情况下安全删除，可以使用-d参数，不过使用-d时，如果分支未合并，删除操作会失败。
