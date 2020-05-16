
## 1. git 基础命令
- git branch
- git checkout
- git clone
- git remote
- git fetch/pull
- git merge
- git reset
- git reflog
- > 参考`廖雪峰 git`

## 2. git客户端
- git shell
- Tortoise Git
- SourceTree

## 3. github fork的项目，别人的项目更新了，怎么更新自己的仓库。有两种方法：
- github上操作，[参考](https://blog.csdn.net/qq1332479771/article/details/56087333)，**反向pull request**
- 本地操作，再push到我的github，[参考](https://github.com/staticblog/wiki/wiki/%E4%BF%9D%E6%8C%81fork%E4%B9%8B%E5%90%8E%E7%9A%84%E9%A1%B9%E7%9B%AE%E5%92%8C%E4%B8%8A%E6%B8%B8%E5%90%8C%E6%AD%A5)，注意选择需要的分支，不一定是master
```shell
git remote -v
git remote add upstream xx(上游仓库地址)
git remote -v

git fetch upstream
git checkout dev
git merge upstream/dev

git push origin dev
```

## 4. github clone wiki
That is, if your repository name was foobar:

git clone git@github.com:myusername/foobar.git would be the path to clone your repository

and

git clone git@github.com:myusername/foobar.wiki.git would be the path to clone its wiki.
- > [参考](https://stackoverflow.com/questions/15080848/how-do-i-clone-a-github-wiki)

## 5. fork项目不会复制wiki。但如果想把wiki也fork过来，怎么办

1. 先clone自己仓库的wiki，再`git remote upstream 别人仓库wiki地址`，[参考：本地操作](#3-github-fork的项目别人的项目更新了怎么更新自己的仓库有两种方法)，再fetch，合并
> 会出现错误git  refusing to merge unrelated histories，google搜索，解决解决方法如下：
```
git merge xx --allow-unrelated-histories
or git pull xx --allow-unrelated-histories
```
操作如下：
```shell
git clone https://github.com/bkunzhang/test-copy-wiki.wiki.git
git remote -v 
git remote add upstream https://github.com/staticblog/wiki.wiki.git
git remote -v

git fetch upstream
git merge upstream/master --allow-unrelated-histories
git push origin master
```
2. 或者先clone别人仓库wiki，再push到自己仓库wiki
```shell
git clone git@github.com:others_username/foobar.wiki.git
git remote add my-fork git@github.com:myusername/foobar.wiki.git
git pull my-fork master --allow-unrelated-histories
解决冲突，commit
git push my-fork master

要使wiki保持同步：
git pull origin master
git push my-fork master
```
- > (参考)(https://codeday.me/bug/20190207/636869.html)

## 6. Issues备份/下载
见<https://github.com/bkunzhang/notes/issues/12>

## 7. github查看commit的时间、邮箱等信息
在url后加.patch，回车即可

## 8. 下载github经常下载不下来，可以只clone最新的版本
git clone git仓库地址 --depth=1

## 9. github执行不了更新操作，不能git clone
需要重新生成ssh key  
 > ssh-keygen -t rsa -C "your@email.com"
 > 打开github设置添加public key即可
 >  ssh -T git@github.com 可以验证是否成功

[参考](https://cloud.tencent.com/developer/article/1572090)