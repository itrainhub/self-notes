## 背景
  项目使用 Angular 框架，版本管理使用的是 Gitlab, 但环境上没有配 node、yarn 等工具，所以计划用 Docker 来做 CI

## 流程



## 思考点

  1. 我们构建一个 pipeline 之后，代码文件会传到 一个目录： `CI_PROJECT_DIR`, 但我们依赖的命令（yarn, npm 等）在 docker 镜像中，如何将文件传入镜像 使其能被操作，是个问题


## 参考链接

  [环境变量](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)