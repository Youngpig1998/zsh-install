Linux下不用翻墙安装zsh及AutoSuggestions插件

一、安装zsh

https://software.opensuse.org/download.html?project=shells%3Azsh-users%3Azsh-autosuggestions&package=zsh-autosuggestions

二、克隆oh-my-zsh到本地（需要先安装git）

执行install.sh脚本

```shell
sh ./install.sh
```

三、切换bash到zsh

```shell
chsh -s $(which zsh)
```

PS: 可以重新打开终端或者先注销再重登试试有没有生效

四、配置.zshrc

将 zsh-autosuggestions文件夹拷贝到~/.oh-my-zsh/plugins文件夹下

```shell
cp -r zsh-autosuggestions ~/.oh-my-zsh/plugins
vim ~/.zshrc
```

在文件里面加入以下脚本

```sh
plugins=( 
    git
    zsh-autosuggestions
)
```

之后使用source命令是配置文件生效

```shell
source ~/.zshrc
```
