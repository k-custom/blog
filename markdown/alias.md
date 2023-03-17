### git alias

#### 查看
> git config --list 

#### 命令设置 alias.别名
> git config --global alias.cm  'commit -m'
> git config --global alias.st  status

#### 文件设置
> 当前  .git/config 文件中添加  [alias] st = status cm = commit -m



#### 取消别名 --unset alias.别名
> git config --global --unset alias.xx

#### 取消别名设置
> git config --global alias.u 'config --global --unset'

