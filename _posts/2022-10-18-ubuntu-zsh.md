---
layout:       post
title:        "Ubuntu配置oh-my-zsh"
author:       "HuFYy"
header-style: Ubuntu
catalog:      true
tags:
    - Ubuntu
    - zsh
    - 主题美化


---

### 安装zsh

```
# 安装 zsh
sudo apt install zsh -y

# 将 Zsh 设置为默认 Shell
chsh -s /bin/zsh

# 可以通过 echo $SHELL 查看当前默认的 Shell，如果没有改为 /bin/zsh，那么需要重启 Shell。
```

### 安装oh-my-zsh

```
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

### 配置oh-my-zsh主题

通过如下命令可以查看可用的`Theme`：

```
# ls ~/.oh-my-zsh/themes
```

编辑`~/.zshrc`文件，将`ZSH_THEME="candy"`,即将主题修改为`candy`。我采用的`yes`

---

关于oh-my-zsh可配置的东西还有很多，**快捷键，颜色，命令提示**等等；后期再更新吧。
