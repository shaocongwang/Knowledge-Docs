# git 版本管理实战命令集合

##---------------------------------------------------------------------------------------------------------------------

###  git 提交流程说明
    $ git add . (添加变更)
    $ git status (查看状态)
    $ git commit -m "interrupt private use delay function comment" (提交并添加提交说明)
    $ git push -u origin master (将提交推送到指定的分支)

### 命令说明

#### 命令1：git fetch origin master
        git fetch ->	从远程下载对象和引用，只更新 .git 目录，不碰工作区文件
        origin ->	远程仓库别名
        master ->	远程分支名

        它把远程 master 的最新位置记录到本地的 origin/master（远程跟踪分支），但你当前分支 master 不动。

#### 命令2:    git log HEAD..origin/master --oneline
        git log ->	查看提交历史
        HEAD..origin/master ->	提交范围：从 HEAD 到 origin/master 之间，但排除 HEAD 能到达的提交
        --oneline  ->	每个提交压缩成一行显示
        关键在 A..B 这个语法：它表示“B 有、A 没有”的提交集合。所以：
        
        HEAD..origin/master → 远程有、本地没有
        
        origin/master..HEAD → 本地有、远程没有

        
#### 命令3：git pull origin master
        git pull	拉取 + 合并，等价于 git fetch 后紧跟 git merge
        origin	远程仓库的默认别名（你 git remote add 时起的名字）
        master	远程仓库里的分支名

        它内部做了两件事
        ① fetch：从 GitHub 下载你本地没有的提交，更新 origin/master
        ↓
        ② merge：把 origin/master 合并进当前分支（你本地的 master）
        
        所以 git pull 是联网 + 改工作区的组合操作。而单独的 git fetch 只做第①步，不改工作区；git merge 只做第②步，不联网。

#### 指定文件提交，推送流程示例
        git add drivers/i2c.h module/stc8h_adc.c
        git commit -m "chore: 移出编译产物和个人配置；更新 i2c.h 与 stc8h_adc.c"
        git push origin master



#### ----------------------------------------------操作实例---------------------------------------------------------------------------------
        shaoc@fala_wang_tp MINGW64 /e/study/SingleChipRoot/workspace/sound_level_stc8h1k17 (master)
        $ git add .

        shaoc@fala_wang_tp MINGW64 /e/study/SingleChipRoot/workspace/sound_level_stc8h1k17 (master)
        $ git status
        On branch master
        Your branch is up to date with 'origin/master'.

        Changes to be committed:
          (use "git restore --staged <file>..." to unstage)
                modified:   module/key_board.c


        shaoc@fala_wang_tp MINGW64 /e/study/SingleChipRoot/workspace/sound_level_stc8h1k17 (master)
        $ git commit -m "interrupt private use delay function comment"
        [master f52d0d2] interrupt private use delay function comment
         1 file changed, 3 insertions(+)

        shaoc@fala_wang_tp MINGW64 /e/study/SingleChipRoot/workspace/sound_level_stc8h1k17 (master)
        $ git status
        On branch master
        Your branch is ahead of 'origin/master' by 1 commit.
          (use "git push" to publish your local commits)

        nothing to commit, working tree clean

        shaoc@fala_wang_tp MINGW64 /e/study/SingleChipRoot/workspace/sound_level_stc8h1k17 (master)
        $ git push -u origin master
        Enumerating objects: 7, done.
        Counting objects: 100% (7/7), done.
        Delta compression using up to 20 threads
        Compressing objects: 100% (4/4), done.
        Writing objects: 100% (4/4), 466 bytes | 466.00 KiB/s, done.
        Total 4 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
        remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
        To https://github.com/shaocongwang/sound_level_stc8h1k17.git
           41e93ce..f52d0d2  master -> master
        branch 'master' set up to track 'origin/master'.

        shaoc@fala_wang_tp MINGW64 /e/study/SingleChipRoot/workspace/sound_level_stc8h1k17 (master)




