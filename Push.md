
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
    -f, --force           강제로 저장소에 업로드합니다.
    --force-with-lease[=<refname>:<expect>]
                          require old value of ref to be at this value
    --recurse-submodules[=<check|on-demand|no>]
                          control recursive pushing of submodules
    --thin                use thin pack
    --receive-pack <receive-pack>
                          receive pack program
    --exec <receive-pack>
                          receive pack program
    -u, --set-upstream    set upstream for git pull/status
    --progress            강제로 진행 상태를 출력합니다. ( stderr는 기본적으로 출력됩니다.)
    --prune               지정한 Refspec 규칙에서 만약 로컬 브랜치가 존재하지 않다면 원격 브랜치도 삭제합니다.
    --no-verify           bypass pre-push hook
    --follow-tags         push missing but relevant tags
    --signed[=<yes|no|if-asked>]
                          GPG sign the push
    --atomic              request atomic transaction on remote side
    -o, --push-option <server-specific>
                          option to transmit
    -4, --ipv4            IPv4 주소만 사용합니다.
    -6, --ipv6            IPv6 주소만 사용합니다.
```
