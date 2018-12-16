# 在你重构之前
[原文链接](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_06/)

有时候程序员需要对现有代码重构。但在此之前你要思考以下几点，这能帮你和他人省去大量处理时间(和痛苦)：
- 重组的最佳方法始于现有代码库的评估及测试。这能够帮你理解当前代码中好和烂的部分，你就能取其精华去其糟粕。我们都认为自己可以做的比现在的系统更好…然后我们交付的东西可能不咋地，甚至更垃圾，因为我们没有从以前系统的缺陷中总结教训。
- 要禁得住推翻重来的诱惑。最大程度地重用现有代码。不论这些代码写得多丑，毕竟它通过了测试和审查等。抛弃旧的代码，尤其是已投入生产使用的，就意味着你正在抛弃历经一个月(或一年)的测试和身经百战的代码，但其中有某些变通和修复bug的方法，只是你不知道而已。如果你不考虑这一点，你写的新代码可能会重现已被旧代码修复过的bug。它们会占用你大量的时间、精力和多年的知识积累。