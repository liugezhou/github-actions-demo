# Introduce
> 本项目使用 create-react-app 脚手架创建，并添加.github/workflows/ci.yml文件，实现项目的 actions 操作。    
>  并记录一些在学习 actions 中的笔记。

# Build
> 项目代码搭建过程：    
> + npm install -g create-react-app   
> + create-react-app  github-actions-demo   
> + cd create-react-app 
> +  打开packages.json文件，加入homepage 字段：「"homepage": "https://[username].github.io/github-actions-demo"」   
> + 在项目根目录下，生成一个 workflow 文件，.github/workflows/ci.yml    

> 以上过程还有 yml 文件的书写，secret 的设置等. 
> 根据 [GitHub Actions 入门教程](http://www.ruanyifeng.com/blog/2019/09/getting-started-with-github-actions.html)

# Note
> 1. Github 把 抓取代码、运行测试、登录远程服务器、发布到第三方服务等操作称为 actions。
> 2. 如果需要某个 action，不必自己写复杂的脚本，直接引用 他人写好的 action 即可，于是整个持续集成的过程，就变成了一个 actions 的组合。这些 actions 可以在仓库  [awesome actions](https://github.com/sdras/awesome-actions)中找到，或者在  [这里](https://github.com/marketplace?type=actions) 搜索。    
> 3. 引用actions的时候比如：actions/setup-node ---这个就表示在 github.com/actions/setup-node 这个仓库，作用是安装 node。    
> 4.  GitHub Actions有一些自己的术语：workflow、job、step、action   
> 5. 配置文件 workflow，采用 YAML 格式，后缀名为.yml，一个库可以有多少 yml 文件，Github 在.github/workfows/下发现有.yml 文件，就会自动运行该文件。  
> 6. workflow 文件的配置字段：  
>  + name: workflow 的名称，若省略，则默认为当前 workflow 的文件名  
> + on: on 字段指定触发 workflow 的条件，比如 on:push,表示 push 事件发生时触发 workflow，on 字段也可以是事件的数组  on: [ push, pull-request ]  
> + branches: 指定触发事件时，可以限定分支或标签    比如 master  main。
> + jobs：每个 jobs 下面可以有多个 job_id(既job的 name) 
> + jobs.job_id.runs-on : jobs.<job_id>.runs-on ：该字段指定运行所需要的虚拟环境,这是必填字段，目前可用的虚拟机有 Ubuntu、window、macOS 
> + jobs.job_id.steps: steps 字段指定每个 Job 的运行步骤，可包含一个或者多个，每个步骤可以指定以下三个字段：name、run、env