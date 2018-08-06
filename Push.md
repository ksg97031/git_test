
# Push

### 용어
- Refspec : https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EB%82%B4%EB%B6%80-Refspec
```sh
$ cat .git/config
...
[remote "origin"]
  url = https://github.com/ksg97031/git_test.git
  fetch = +refs/heads/*:refs/remotes/origin/*
...
```

### 옵션 설명
```sh
usage: git push [<options>] [<repository> [<refspec>...]]

    -v, --verbose         더욱 자세한 진행 메시지 출력
    -q, --quiet           더욱 조용하게 진행 메시지 출력
    --repo <repository>   저장소(원격저장소)
    --all                 모든 로컬 브랜치들을 저장소에 업로드합니다.
    --mirror              모든 로컬 브랜치들을 저장소에 미러링합니다. (주의! 충돌이 발생해도 강제로 업로드합니다.)
    -d, --delete          저장소에 해당 브랜치를 삭제합니다. ('git push origin :브랜치명' 명령어와 동일합니다.)
    --tags                로컬 저장소에서 만든 모든 태그들을 저장소에 업로드합니다.
    -n, --dry-run         업로드(Push)와 관련된 모든 행동을 테스트합니다. 실제 업데이트가 이루어지진 않습니다.
    --porcelain           refs의 실제 심볼릭명이 출력됩니다. (머신이 읽기 편하게 출력 라인이 탭으로 구분되어 있습니다.)
    -f, --force           강제로 커밋을 저장소에 업로드합니다.
    --force-with-lease[=<refname>:<expect>]
                          추가로 생성된 커밋에 병합 없이는 강제로 저장소에 업로드하지 않습니다.(force보단 이 옵션을 추천합니다.)
    --recurse-submodules[=<check|on-demand|no>]
                          on-demand: 서브모듈을 모두 업로드합니다. check: 서브모듈이 커밋되지 않으면 실패를 반환합니다.
    --thin                thin pack으로 업로드합니다.(더 적은 횟수로, 적은양의 오브젝트를 전송하는 방식입니다. 느린 네트워크 속도에 좋습니다,)
    --receive-pack <receive-pack> \
    --exec <receive-pack>
                          리모트에 있는 git-receive-pack 프로그램을 가져옵니다.
    -u, --set-upstream    set upstream for git pull/status
    --progress            강제로 진행 상태를 출력합니다. ( stderr는 기본적으로 출력됩니다.)
    --prune               지정한 Refspec 규칙에서 만약 로컬 브랜치가 존재하지 않다면 원격 브랜치도 삭제합니다.
    --no-verify           pre-push 훅 기능을 사용하지 않습니다.
    --follow-tags         태그들과 같이 푸쉬합니다. git 2.4.1 버전 이상부터 기본으로 활성화되어 있습니다.
    --signed[=<yes|no|if-asked>]
                          GPG sign the push
    --atomic              request atomic transaction on remote side
    -o, --push-option <server-specific>
                          pre-receive, post-receive 훅에 옵션으로 전달되며 해당 옵션이 없을시 기본으로 설정에 push.pushOption이 대신합니다.
    -4, --ipv4            IPv4 주소만 사용합니다.
    -6, --ipv6            IPv6 주소만 사용합니다.
```

### 학습
```sh
ex) git push {remote} {branch}

$ git remote
origin

$ git branch
* master

$ git push origin master
Counting objects: 5, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (5/5), 520 bytes | 520.00 KiB/s, done.
Total 5 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/ksg97031/git_test.git
```

```sh
ex) git push {remote} {branch} tags

$ git tag
100
200

$ git tag 300
$ git tag
100
200
300

$ git push origin master --tags
Total 0 (delta 0), reused 0 (delta 0)
To https://github.com/ksg97031/git_test.git
 * [new tag]         300 -> 300
 
$ git log
commit 0b3fea39602569f627e304231cb7580caf6c0887 (HEAD -> master, tag: 300, origin/master, origin/HEAD)
... 
...
```

```sh
ex) git push {remote} -d {branch}

$ git branch
  hi
* master

$ git push origin -d hi
To https://github.com/ksg97031/git_test.git
 - [deleted]         hi
 
$ git branch -d hi 
Deleted branch hi (was c10d33f).
```

```sh
ex) git push {remote} {branch} {force-option}

$ git show
~
$ git reset head~
$ git add .; git commit -am "previous recommit"
$ git push origin master --force-with-lease
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 834 bytes | 834.00 KiB/s, done.
Total 3 (delta 2), reused 0 (delta 0)
remote: Resolving deltas: 100% (2/2), completed with 2 local objects.
To https://github.com/ksg97031/git_test.git
 + 0b3fea3...b42b62b master -> master (forced update)
```

