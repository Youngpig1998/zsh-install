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




















# Note: This dropin only works with kubeadm and kubelet v1.11+
[Service]
Environment="KUBELET_KUBECONFIG_ARGS=--bootstrap-kubeconfig=/etc/kubernetes/bootstrap-kubelet.conf --kubeconfig=/etc/kubernetes/kubelet.conf"
Environment="KUBELET_CONFIG_ARGS=--config=/var/lib/kubelet/config.yaml"
# This is a file that "kubeadm init" and "kubeadm join" generates at runtime, populating the KUBELET_KUBEADM_ARGS variable dynamically
EnvironmentFile=-/var/lib/kubelet/kubeadm-flags.env
# This is a file that the user can use for overrides of the kubelet args as a last resort. Preferably, the user should use
# the .NodeRegistration.KubeletExtraArgs object in the configuration files instead. KUBELET_EXTRA_ARGS should be sourced from this file.
EnvironmentFile=-/etc/sysconfig/kubelet
ExecStart=
ExecStart=/usr/bin/kubelet $KUBELET_KUBECONFIG_ARGS $KUBELET_CONFIG_ARGS $KUBELET_KUBEADM_ARGS $KUBELET_EXTRA_ARGS