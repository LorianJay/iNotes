# 目录  
1.nodejs基本介绍  


## 1.nodejs基本介绍  
**目录**  
1.1 nvm  
1.2 node  

### 1.1 nvm  
**目录:**  
1.1.1 nvm官网  
1.1.2 nvm安装  
1.1.3 验证安装  
1.1.4 卸载nvm(手动卸载)  
1.1.5 安装node  
1.1.6 验证node安装完成  

#### 1.1 nvm安装  
1.前往官网找到详细的安装命令[nvm官网](https://github.com/nvm-sh/nvm)  

#### 1.1.2 nvm安装
执行安装/更新脚本  
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash`  
`wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | bash`  
上述脚本二选一即可,另外如果是要更新nvm也可以去官网找到最新的脚本然后更新  

*脚本功能:*  
上述脚本会克隆nvm仓库到`~/.nvm`文件夹下,并且会将下面这段代码行添加到对应的配置文件中(`~/.bashrc`),如果安装脚本正在更新错误的配置文件,则需要通过设置环境变量`$PROFILE`为正确的配置文件路径,然后重新执行脚本  
```console
export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
```
#### 1.1.3 验证安装
当安装脚本执行完毕之后执行`source ~/.bashrc`命令,然后再执行`command -v nvm`看是否输出nvm即可,如果输出代表安装成功  

#### 1.1.4 卸载nvm(手动卸载)  
1.在命令行执行以下命令  
```console
nvm_dir="${NVM_DIR:-~/.nvm}"
nvm unload
rm -rf "$nvm_dir"
```

2.编辑`~/.bashrc`文件,并移除下面这些行  
```console
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm
[[ -r $NVM_DIR/bash_completion ]] && \. $NVM_DIR/bash_completion
```

#### 1.1.5 安装node  
1.安装最新版本  
`nvm install node`  

2.安装特定版本  
`nvm install v20.20.2`  

3.查看所有版本  
`nvm ls-remote`  

4.查看所有LTS版本  
`nvm ls-remote --lts`  

5.使用node(选择node版本)  
`nvm use v20.20.2`  

6.查看所有已经安装的版本  
`nvm ls`  

7.查看当前使用的版本  
`nvm current`  

8.全局选择node版本  
`nvm alias default v24.17.0`
方式5切换到node版本只针对当前终端生效,正确的切换命令应该是用当前命令

#### 1.1.6 验证node安装完成  
执行`node --version`即可  

### 1.2 node  




