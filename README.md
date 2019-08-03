# 我的博客 - 金鱼的记忆仓库

![CI Status](https://travis-ci.org/megabitsenmzq/megabitsenmzq.github.io.svg?branch=source) ![Hugo](https://img.shields.io/badge/With-Hugo-yellow)

**博客内文章版权所有，如想转载请先与我联系。此分支内容为 Hugo 源文件。**

### 使用

Hugo: [https://gohugo.io/](https://gohugo.io/)

Paper Theme: [https://github.com/nanxiaobei/hugo-paper/](https://github.com/nanxiaobei/hugo-paper/)

Travis CI: [https://travis-ci.org/](https://travis-ci.org/)

### CI 自动构建脚本

```
language: go

cache:
  directories:
    - $HOME/.cache/go-build
    - $HOME/gopath/pkg/mod
    - $HOME/gopath/src

git:
  depth: 1

install: go get -v github.com/spf13/hugo

script:
  - hugo
  
before_cache:
  - rm -rf !(public)

deploy:
  provider: pages
  skip_cleanup: true
  # token is set in travis-ci.org dashboard
  github_token: $GITHUB_API_KEY
  on: source
  local_dir: public
  repo: megabitsenmzq/megabitsenmzq.github.io
  target_branch: master
  email: deploy@travis-ci.org
  name: deployment-bot
```