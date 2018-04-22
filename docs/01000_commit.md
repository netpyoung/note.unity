commit
======================



# change log
* Semantic Versioning 2.0.0
  - http://semver.org/

* http://keepachangelog.com/en/1.0.0/

* `Added` : for new features.
* `Changed` : for changes in existing functionality.
* `Deprecated` : for soon-to-be removed features.
* `Removed` : for now removed features.
* `Fixed` : for any bug fixes.
* `Security` : in case of vulnerabilities.


## sample

```
Fixed: #123
```



## Etc
* Need to seperate code commit and resource commit message.
  - because designer also using git, so we need special prefix/postfix for code commit message.



# How to review





git branch model
http://nvie.com/posts/a-successful-git-branching-model/

git branch rebase
http://git-scm.com/book/ko/v1/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase%ED%95%98%EA%B8%B0



```
# rename git branch locally and remotely
# https://gist.github.com/lttlrck/9628955

    git branch -m old_branch new_branch         # Rename branch locally    
    git push origin :old_branch                 # Delete the old branch    
    git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote
```