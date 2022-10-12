+++
title = "基于Org的GTD实践"
date = 2020-11-05T13:17:00+08:00
lastmod = 2020-11-09T14:51:42+08:00
draft = false
summary = "在这篇文章中，我将详细介绍如何使用Orgmode实现GTD，而不是解释GTD方法本身或Orgmode是如何工作的。"
+++

> 原文作者: Nicolas Petton
>
> 原文链接: <https://emacs.cafe/emacs/orgmode/gtd/2017/06/30/orgmode-gtd.html>


## 引言 {#引言}

在过去的4年里，我一直在使用[Orgmode](http://orgmode.org/)来实现[GTD方法](https://en.wikipedia.org/wiki/Getting%5FThings%5FDone)。

在这篇文章中，我将详细介绍如何使用Orgmode实现GTD，而不是解释GTD方法本身或Orgmode是如何工作的。

如果您不了解Orgmode并对其感兴趣，您应该先访问其[网站](http://orgmode.org/)。


## orgmode文件 {#orgmode文件}

我将GTD拆分为四个单独的文件：

-   `inbox.org` ：我收集所有东西的地方；
-   `gtd.org` ：放置所有项目的位置；
-   `someday.org` ：所有我可能在将来某个时候完成但不想一直看到的非当前活动任务；
-   `tickler.org` ：我在此文件中放置了带有[时间戳](http://orgmode.org/manual/Timestamps.html)的条目，以便在正确的时间得到提醒。

将这些文件添加到议程文件非常重要(稍后将详细介绍议程)，如下所示：

```lisp
(setq org-agenda-files '("~/gtd/inbox.org"
                         "~/gtd/gtd.org"
                         "~/gtd/tickler.org"))
```


## 1. GTD收件箱 {#1-dot-gtd收件箱}

GTD最重要的一个方面是收件箱。每一个想法都应该在那里收集起来，然后再进行处理。

{{< figure src="https://grass.show/blog-pic/img/20201105133119.png" >}}

Org模式有一个非常好的特性，非常适合这个概念：[org-capture](http://orgmode.org/manual/Capture.html)。

只需按一个按键即可捕获思想：只需按 `C-c c` ，捕获弹出窗口就会出现在Emacs中。一旦您完成捕获，使用 `C-c C-c` 将它存储在收件箱中。

{{< figure src="https://grass.show/blog-pic/img/20201105133204.png" >}}

下面是我的设置方式：

```lisp
(setq org-capture-templates '(("t" "Todo [inbox]" entry
                               (file+headline "~/gtd/inbox.org" "Tasks")
                               "* TODO %i%?")
                              ("T" "Tickler" entry
                               (file+headline "~/gtd/tickler.org" "Tickler")
                               "* %i%?\n %U")))
```

[此处](http://orgmode.org/manual/Capture-templates.html#Capture-templates)介绍了捕获模板的语法。它提供了很多定制选项。

按 `C-c c t` 将条目添加到我的收件箱，按 `C-c c T` 将条目添加到记事本(稍后将详细介绍)。

下面是我的收件箱的样子：

{{< figure src="https://grass.show/blog-pic/img/20201105133221.png" >}}

然后，我的收件箱每天都会被处理和清空。在处理收件箱时，我把每一个可执行且属于某个项目的条目使用 `C-c C-w` [转接](http://orgmode.org/manual/Refile-and-copy.html#Refile-and-copy)，并将条目移动到适当的位置。如果需要，我会用它创建一个新项目。

我已经按如下方式设置了转接目标：

```lisp
(setq org-refile-targets '(("~/gtd/gtd.org" :maxlevel . 3)
                           ("~/gtd/someday.org" :level . 1)
                           ("~/gtd/tickler.org" :maxlevel . 2)))
```

因此 `C-c C-w` 会提示我选择一个项目、备忘录或将来/也许清单。


## 2. 项目文件 {#2-dot-项目文件}

我的主文件是 `gtd.org` 。那是我保存所有正在进行的项目的地方。我通常在同一时间有大约30个正在进行的项目。

每个项目都包含要执行的行动。每个项目的第一个行动被称为“下一步行动”，这也是我在处理项目时总是要做的。一旦任务完成，我就使用 `DONE` 关键字对其进行标记。

以下是一个示例项目：

您在屏幕截图上看到的完成百分比是[Orgmode的另一个出色的功能](http://orgmode.org/manual/Checkboxes.html)：)


### 标签 {#标签}

标签是在标题上使用 `C-c C-c` 完成的，无论它是项目还是行动。我使用标签有几个目的：

-   常规类别，如 `:emacs:` 或 `:writing:` ；
-   链接到人的标签，如 `:daniel:` ；
-   GTD上下文。

GTD上下文只是一个以 `@` 开始的常规标签。我在[自定义Org议程命令](http://orgmode.org/worg/org-tutorials/org-custom-agenda-commands.html)中大量使用它们。

我的上下文往往会随着时间的推移而变化，但我始终至少使用 `@home` ,
`@office` , `@travelling` , `@phone` , `@email` ,
`@errands` ,以根据我当前的位置筛选出下一步行动。


### TODO关键字 {#todo关键字}

我在所有项目条目中都放了一个关键字。我想我主要使用相当常规的关键字： `TODO` 、 `WAITING` 、 `DONE` 和 `CANCELLED` 。前两个用于未完成状态，后两个用于已完成状态。

```lisp
(setq org-todo-keywords '((sequence "TODO(t)" "WAITING(w)" "|" "DONE(d)" "CANCELLED(c)")))
```

在标题上，按 `C-c C-t` 设置TODO关键字。


### 时间戳、日程安排和截止日期 {#时间戳-日程安排和截止日期}

我倾向于尽量避免在我的项目中使用时间戳。原因很简单：除非条目是预约的(例如去看牙医)，或者有固定的截止日期(与客户安排的发布)，否则我应该根据当前的上下文(以及其他事情)来决定要做什么。这也让我的议程保持干净，没有任何虚假的或自我强加的最后期限或时间表。

但日程安排有时是有意义的。为此，请在条目上按 `C-c C-s` ，然后输入日期或时间。若要添加截止日期，请按 `C-c C-d` 。请注意，Orgmode在如何输入日期方面非常聪明，如果你不会使用，请参阅[使用手册](http://orgmode.org/manual/Deadlines-and-scheduling.html)。


### 筛选项目和行动 {#筛选项目和行动}

当决定要处理什么时，我会使用[稀疏树](http://orgmode.org/manual/Sparse-trees.html)——这使得通过标签、搜索词等过滤我的GTD项目内容变得很容易，或者我使用[自定义议程命令](http://orgmode.org/worg/org-tutorials/org-custom-agenda-commands.html)。在发现Orgmode时，大多数人认为它的议程只是一个常规议程。当然，它拥有每天(每周)日程安排，但它提供的远不止这些。引用手册内容：

>
>
> Org-mode的内置议程命令是搜索笔记以及收集、排序、过滤和显示任务的强大工具。

我使用自定义议程命令主要是为了根据上下文或标签获得行动概述。下面是一个自定义议程命令示例，它将显示 `@office` 上下文的所有行动：

```lisp
(setq org-agenda-custom-commands
      '(("o" "At the office" tags-todo "@office"
         ((org-agenda-overriding-header "Office")))))
```

遵循GTD原则，我通常希望使用 `@office` 标签为每个项目仅显示要完成的/首要行动/(或下一步行动)。

这可以使用跳过条件来实现：

```lisp
(setq org-agenda-custom-commands
      '(("o" "At the office" tags-todo "@office"
         ((org-agenda-overriding-header "Office")
          (org-agenda-skip-function #'my-org-agenda-skip-all-siblings-but-first)))))

(defun my-org-agenda-skip-all-siblings-but-first ()
  "跳过除第一个未完成条目之外的所有条目。"
  (let (should-skip-entry)
    (unless (org-current-is-todo)
      (setq should-skip-entry t))
    (save-excursion
      (while (and (not should-skip-entry) (org-goto-sibling t))
        (when (org-current-is-todo)
          (setq should-skip-entry t))))
    (when should-skip-entry
      (or (outline-next-heading)
          (goto-char (point-max))))))

(defun org-current-is-todo ()
  (string= "TODO" (org-get-todo-state)))
```

创建自定义议程命令一开始可能有点棘手，一种简单的方法是通过 `M-x customize-variable RET org-agenda-custom-commands` 对它们进行自定义。

若要选择要执行的议程命令，请按 `C-c a` 。


## 3. “将来/也许”清单 {#3-dot-将来-也许-清单}

您是否注意到 `someday.org` 不是 `org-agenda-files` 中设置的议程文件的一部分？

这是因为我不希望看到此文件中的任何条目出现在我的议程缓冲区中，除非我正在进行每周审查。这正是“将来/也许”名单的目的。

这份文件应该每周审查一次，作为每周审查的一部分(我在周日晚上做这件事)。

在每周审查期间，我在“正在进行”状态(在 `gtd.org` 中)和“将来/也许”状态(在 `someday.org` 中)之间来回移动项目。

例如，如果一个项目已经前进到某个点，但我知道由于某种原因它会停滞几周，我会将其移到 `someday.org` 。在以后的每周审查期间，我会将其移回 `gtd.org` ，届时它将再次变为正在进行状态。

为了移动项目，我还使用转接。


## 4. 备忘录 {#4-dot-备忘录}

在我看来，备忘录是GTD最好的概念之一。

比方说你一个月后得付账单。如果你不想错过截止期限，你需要把它写在你的GTD里。但是你也不想每次浏览你的GTD项目时都被提醒：因为现在不是付钱的时候。

这就是备忘录的作用：在您的备忘录文件中添加一个带有时间戳的条目，然后忘掉它！

当时间到来时，该操作将出现在您的Org议程中，提醒您必须支付的账单，您所要做的就是将其移动到您的收件箱中。在那之前，你可以把注意力放在别的事情上，把你的思想从这项任务中解放出来。


## 引用文件 {#引用文件}

所有引用文件都放在我的Orgmode文件旁边的 `references` 文件夹中。然后将它们从Dired缓冲区链接(使用 `org-store-link` )到我的项目中，以便快速访问。

我还使用 `org-store-link` 链接电子邮件(如果我碰巧在Emacs中看到了它们)。


## 归档 {#归档}

在每周审查期间，我使用 `C-c C-x C-a` ( `org-archive-subtree-default` )将已完成的项目存档，它将条目移动到存档文件。

这样，我的GTD文件就会保持整洁，而且我永远不会删除任何数据。


## 结尾 {#结尾}

这是一个非常广泛的主题，所以显然我没有涵盖所有内容，但我希望这解释了我如何使用Orgmode实现GTD的基础知识。

这实际上知识我个人的方法。Orgmode是一个具有可塑性的的工具，我不认为有两个完全相同的设置。