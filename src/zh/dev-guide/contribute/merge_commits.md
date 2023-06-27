---
order: 4
---

# 合并提交

如果您提交了一个PR以后，根据检视意见完成修改并再次提交了PR，您不想让审阅者看到多次提交的PR，因为这不便于继续在检视中修改，那么您可以合并提交的PR。合并提交的PR是通过压缩Commit来实现的。

1、现在本地分支上查看日志

```bash
git log
```

2、然后把顶部的n个提交记录聚合到一起进入，注意n是一个数字。

```bash
git rebase -i HEAD~n
```

把需求压缩的日志前面的pick都改成s，s是squash的缩写。注意必须保留一个pick，如果将所有的pick都改成了s就没有合并的目标了，会发生错误。

3、修改完成以后，按ESC键，再输入`:wq`，会跳出一个界面，问你是否进入编辑提交备注的页面，输入e以后，进入合并commit message的页面。请把需要合并的message都删掉，只保留合并目标的message，再按ESC键，输入`:wq`保存退出即可。

4、最后完成提交

```bash
git push -f origin yourbranch
```

5、回到github上的PR提交页面查看，您就可以看到之前的提交已经合并了。