# linux 软件安装

[TOC]

**拓展组件安装需要在root权限下进行。**

## 基础拓展软件

#### vim 安装与使用

$~~~~~$ vim 是从 vi 发展出来的一个文本编辑器。代码补完、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用。

$~~~~~$ 简单的来说， vi 是老式的字处理器，不过功能已经很齐全了，但是还是有可以进步的地方。 vim 则可以说是程序开发者的一项很好用的工具。

<font size=4 color="DarkViolet">vim 安装</font>

vim安装只需要一段安装代码，不用调试东西

```linux
# apt-get install vim
```

<font size=4 color="DarkViolet">vim 使用</font>

只需要把打开文件进行编辑的命令 **`vi`** 替换成 **`vim`** 就行了

如：

```linux
# vi 这样打开文件
vi [文件]

# vim这样打开文件
vim [文件]
```

#### sudo 安装与使用

Linux sudo 命令以系统管理者的身份执行指令，也就是说，经由 sudo 所执行的指令就好像是 root 亲自执行。

使用权限：在 /etc/sudoers 中有出现的使用者。

<font size=4 color="DarkViolet">sudo 安装</font>

1. 安装需要如下命令

   ```linux
   # apt-get install sudo
   ```

   安装完成后，需要给用户权限，要在 /etc/sudoers 文件中修改：

2. 修改 /etc/sudoers 文件属性为可写

   ```linux
   # chmod +w /etc/sudoers
   ```

3. 编辑 /etc/sudoers

   ```linux
   # vim /etc/sudoers
   ```

   添加如下行:

   ```linux
   user ALL=(ALL) ALL # 用户user执行sudo时需要密码。
   # user ALL=NOPASSWD:ALL  用户user执行sudo时不需要密码。
   # user ALL=NOPASSWD:/etc/network/interfaces   用户user执行只有 sudo 执行/etc/network/interfaces的权限，执行时不需要密码。
   ```

   哪个账户需要权限 user 就填哪个账户。

4. 修改 /etc/sudoers 文件属性为只读

   ```linux
   # chmod -w /etc/sudoers
   ```

<font size=4 color="DarkViolet">sudo 使用</font>

sudo 指定的用户可以通过在执行代码前加上 sudo 来以 root 方式执行,如：

```linux
# 我们原来需要在 root 账户这样设置文件读取权限
chmod +w [文件名]

# 现在我们可以在 sudo 指定的普通账户中这样设置文件读取权限
sudo chmod +w [文件名]
```

其他的都可以以此类推，需要 root 权限的大部分都可以通过加前缀 sudo 进行执行，但有小部分必须是 root 账户才能 sudo 无法获取到这些权限。

#### BBR 算法

$~~~~~$ TCP 拥塞控制算法 BBR (Bottleneck Bandwidth and RTT) 可以大限度地利用服务器带宽，减少排队的情况，提高网络质量。

<font size=4 color="DarkViolet">BBR 启用</font>

1. 首先，我们通过以下两段代码开启 BBR 算法

   ```shell
   echo net.core.default_qdisc=fq >> /etc/sysctl.conf
   echo net.ipv4.tcp_congestion_control=bbr >> /etc/sysctl.conf
   ```

   然后，使用 `sysctl -p` ，将其保存并生效

2. 查看内核是已经开启 BBR

   ```shell
   sysctl net.ipv4.tcp_available_congestion_control
   ```

   若返回值中包含以下代码，说明成功开启

   ```shell
   net.ipv4.tcp_available_congestion_control = reno cubic bbr
   ```

3. 查看 BBR 是正在运行

   ```shell
   lsmod | grep bbr
   ```

   若有返回值，说明正在运行中。

## 其他拓展软件

#### jdk
