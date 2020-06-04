# Git

**#neverforget [git da moçada](https://docs.google.com/presentation/d/1bStodKV1rOdAQ-8RrG4wJeRY_5RIpy_PsR9PbHci5eE/edit#slide=id.p)**

**Always use small commits, specific for each separate task you are doing. This is necessary in order to:.**

* Create a consistent history of changes in the repo, making it easy for other developers to understand what was going on at a given period of time
* Make it easier to revert specific changes if that is ever necessary
* More about this [here](https://www.notion.so/natahouse/Commit-best-practices-4f51db54000e4b93b9701931b58b58e8)
* Or in english [here](https://github.com/trein/dev-best-practices/wiki/Git-Commit-Best-Practices#examples-of-good-practice)

**Always use rebase to update your feature branches before merging into develop. This helps maintain a clear history and prevents overly complicated merge conflicts. However, be careful to NEVER rebase a branch that is being used by someone other than yourself, that could cause very difficult issues to solve.**

**Avoid creating *staging* branches that cannot be merged into *master*, try to configure the differences between the environments in places other than the source code itself. This makes your delivering process much easier and reduces the risk for conflicts drastically.**
