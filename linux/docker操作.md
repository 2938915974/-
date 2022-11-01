# docker 基础操作

[TOC]

## docker安装与卸载

1. **旧版本卸载**

   旧版本的卸载 (第⼀次安装可直接跳过)
   如果安装翻⻋过⼀次，那么第⼆次安装需要卸载第⼀次的操作，执⾏如下指令可进⾏卸载操作：

   ```shell
   apt remove docker docker-engine docker.io containerd runc
   ```

2. **仓库源添加**

   这⼀步是向 Linux 的更新源⾥添加 Docker 的官⽅仓库源，便于更新操作。

   1. 添加包索引

      执⾏如下指令即可：

      ```shell
      # Linux 下⾸次安装软件前，需更新包的索引，若想更新系统或者软件，可执⾏ apt update && apt upgrade -y
      apt update

      # 添加必要的包以使⽤HTTPS仓库
      apt install \
      apt-transport-https \
      ca-certificates \
      curl \
      gnupg \
      lsb-release
      ```

   2. 添加 GPG

      通过如下指令添加 Docker 官⽅ GPG密钥：

      ```shell
      # 注意，如果你使⽤的是⾮ root 帐号，那么你需要执⾏注释中的这段，否则执⾏⾮注释⽚段。
      # sudo curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

      curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
      ```

   3. 添加稳定仓库

      执⾏如下指令可完成添加

      ```shell
      # 如果你是⾮ root 账⼾，那么执⾏注如下⽚段:
      echo \
      "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
      $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

      # 如果你是 root 帐号，执⾏如下指令:
      echo \
      "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
      $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
      ```

3. **docker部署**

   如上我们添加好仓库地址后，我们执⾏如下指令 完成 Docker 的安装部署：

   ```shell
   # 添加了新的仓库后，我们需要⽴刻更新 apt 源
   apt update

   # 然后执⾏安装操作
   apt install docker-ce docker-ce-cli containerd.i
   ```

## docker 容器的启动、卸载、暂停

<font size=4 color="DarkViolet">容器启动与进入容器</font>

首先，我们搜索所有的容器

``` docker
docker ps -a
```

然后，启动镜像，若镜像已经启动了就跳过此步

```shell
docker start 容器ID
```

进入正常启动的镜像

```shell
docker exec -it [容器名或者 ID] bash
```

<font size=4 color="DarkViolet">docker 容器关闭</font>

## docker 中各类容器的安装与操作

$~~~~~$ 通常来说，我一般将docker 容器的持久化映射放在 `/usr/mydocker` 中

在 docker 中，有许多通用的容器配置选项，下面将一一介绍出来
> 容器配置通常是在第一次 run 的时候配置的，称为初始化运行

1. 端口映射

   ```shell
   --publish [物理机端口号]:[容器内端口号]
   ```

   $~~~~~$ 作用是将容器内部的端口映射到物理机上。映射完成后，访问容器该物理机端口就会映射到容器内部对应的端口。

2. 持久化映射

   ```shell
   --volume /usr/mydocker/gitlab/data:/var/opt/gitlab
   ```

   $~~~~~$ 作用是将容器的文件目录映射到物理机上，其实就是容器实时操控两个文件系统，一个容器内的，一个物理机的，当容器内该文件目录下有改动，就会去改动物理机的数据。
   > $~~~~~$ 持久化映射并不是必要的，而且很多时候是将文件映射到另一个专门储存的容器，这样除非出现让整个 docker 都崩了的情况，不然数据还是很安全的。

3.

#### Gitlab 安装与操作

<font size=4 color="DarkViolet">Gitlab 安装</font>

1. **Gitlab镜像拉取**

   ```shell
   docker pull gitlab/gitlab-ce
   ```

2. **持久化配置**

   持久化需要把数据映射到物理机上，这样 docker 崩了数据还在。

   1. **物理映射地址创建**

      为了能成功映射我们容器内的⽂件到物理机上，我们需要提前在物理机中指定相应的⽂件夹，如我们需要映射 config 、data 、logs 三个⽬录下的数据，那么我们则需要在任意⽬录创建这3个目录 ：

      ```shell
      # 1. 在 /usr ⽬录中创建 gitlab ⽂件夹并进入

      sudo mkdir /usr/mydocker/gitlab ; cd /usr/mydocker/gitlab

      # 2. 我们在 gitlab ⽂件夹中创建 3 个⽬录

      # 2.1. config ⽬录用于映射 gitlab 容器的 config 配置⽂件⽬录
      sudo mkdir config

      # 2.2. data ⽬录用于映射 gitlab 容器的 data 数据⽂件⽬录
      sudo mkdir data

      # 2.3. logs ⽬录用于映射 gitlab 容器的 logs ⽇志⽂件⽬录
      sudo mkdir logs
      ```

      最后我们需要给 gitlab ⽂件夹予以⼀定的权限 ：

      ```shell
      sudo chmod -R 777 /usr/mydocker/gitlab
      ```

   2. **携带持久化方案的初始化镜像设置**

      通过 -v 参数将容器内部的⽂件 持久化（映射）到物理机上，同时初始化镜像：

      ```shell
      docker run -it \
      --publish 2010:80 --publish 2011:443 --publish 2012:22 \
      --name gitlab \
      -m 4G \
      --cpus=2 \
      --volume /usr/mydocker/gitlab/logs:/var/log/gitlab \
      --volume /usr/mydocker/gitlab/data:/var/opt/gitlab \
      --volume /usr/mydocker/gitlab/config:/etc/gitlab \
      --restart=always -d gitlab/gitlab-ce
      ```

      **上述指令集中，我们在如下分段解释:**

      - **`docker run -it \`** : 指 docker 通过 run 指令启动并初始化，并且希望通过 -it 参数能进⼊容器。
      - **`--publish 2010:80`** : 可简写为 -p，这⾥冒号 " : " 左边为物理机的端口，右边为容器内的端口。
      - **`--name`** 可当前容器命名别名
      - **`-m 4G`** 容器内的镜像通常会无上限的使用物理机的运行内存，所以这里需要给予⼀定的限制。
      - **`--cpus=2`** 给容器内的镜像限制 CPU核心数。
      - **`--volume`** 这⾥可以简写为 -v ，其中 $PWD/xx 代表当前路径下的xx⽂件夹中，冒号右边是容器内的目录。
      - **`--restart=always`** 这里指当 Docker 重启、服务器重启的时候会自动重启有该参数的容器。
      - **`-d gitlab/gitlab-ce`** : 这里指将镜像挂载到后台运行。

3. **Gitlab 相关配置**

   虽然上面配置很多东西我们也初始化了Gitlab，但是还是不能直接启动，需要先修改特定配置

   先进入gitlab文件目录：

   ```shell
   cd /usr/mydocker/gitlab/
   ```

   1. **Config文件修改**

       我们需要修改位于 物理机中的 gitlab ⽂件夹⽬录中的 config ⽬录下的 gitlab.rb 配置⽂件，通过 vi 打开：

       ```shell
       sudo vi config/gitlab.rb
       ```

       通过 vi 打开后，我们找到 external_url 配置项，该选项是我们容器中 http 访问的端口，我们需要将其修改为我们的物理机的IP地址：

      ```rb
      ## GitLab URL
      ##! URL on which GitLab will be reachable.
      ##! For more details on configuring external_url see:
      ##! https://docs.gitlab.com/omnibus/settings/configuration.html#configuring-theexternal-url-for-gitlab
      ##!
      ##! Note: During installation/upgrades, the value of the environment variable
      ##! EXTERNAL_URL will be used to populate/replace this value.
      ##! On AWS EC2 instances, we also attempt to fetch the public hostname/IP
      ##! address from AWS. For more details, see:
      ##! https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instancedata-dataretrieval.html
      external_url 'http://这⾥是你的物理机器IP地址:80'
      ```

      **注意:** : 这里的物理机 IP 地址，在实际企业中必定填写物理机的IP地址，在虚拟机中，每次虚拟机重启都会修改 IP 地址，那么我们要么就给虚拟机固定 IP 地址，要么我们可以尝试将 IP 地址改为 127.0.0.1，但是有可能不行，这时只能将就每次都查一下虚拟机的地址了。
      > 此处的端口号是容器内部的端口号，需要保证与启动配置的映射出去的端口号保持一致，不然外部将无法访问该容器。

   2. **生效后的配置文件**

      首先我们需要给予 data 目录⼀定的权限，就算我们之前已经赋予了权限，但是 gitlab 会为了保证安全性，依旧会刷新权限，为避免我们修改，但是为了便于我们查看，我们首先将 data 目录给予权限：

      ```shell
      sudo chmod -R 777 data
      ```

      授予权限后，我们要尽快通过如下指令查看配置⽂件项：

      ```rb
      # gitlab 的配置⽂件以 yml 显⽰
      $ sudo vi data/gitlab-rails/etc/gitlab.yml
      # 我们可以看到类似如下配置所⽰
      production: &base
      #
      # 1. GitLab app settings
      # ==========================
      ## GitLab settings
      gitlab:
      ## Web server settings (note: host is the FQDN, do not include http://)
      host: 这⾥的 IP 地址已经变成了我们在 config 中修改的IP地址
      port: 80
      https: false
      ```

   3. **重启 gitlab**
       ⼀切⼯作准备就绪后，我们可重启 Gitlab 以查看效果：

       ```shell
       sudo docker restart gitlab的容器ID
       ```

<font size=4 color="DarkViolet">GitLab 使用</font>

启动后，我们在浏览器中尝试通过以下几种链接访问访问 gitlab ：

```url
http://localhost:2010/

http://127.0.0.1:2010/

http:// ip地址 :2010/
```

如果还不行，那凉了，具体问题查看启动日志：

```shell
docker logs [gitlab容器的id]
```

成功了会跳出gitlab的修改密码界面或者登陆界面，我们通过以下代码获取默认密码

```shell
docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
```

获取到密码后就可以直接登录了，账户名 `root` 或 `admin@example.com` 都可以。
账号为管理员账号，登录后记得及时修改密码

向 Gitlab 提交项目不像 GITHUB 一样，GITHUB 直接向 GITHUB 地址提交，gitlab是向内部服务器提交（如果你有域名，也可以直接向域名提交），所以需要服务器 ipv4 地址与 gitlab 的端口。

如在githud中我们这样获取代码：

```git
https://github.com/2938915974/spring-clould-001.git
```

在gitlab中就需要这样获取：

```git
http://192.168.27.138:2010/2938915974/spring-clould-001.git
```

#### mysql 安装与操作

<font size=4 color="DarkViolet">mysql 安装</font>

1. **查询 mysql 软件的 docker images ：**

    ```shell
    docker search mysql
    ```

2. **拉取（下载）所有查询到的 mysql ：**

    ```shell
    docker pull mysql
    ```

3. **查看 docker 的本地镜像，看 mysql 有没有下载**

    ```shell
    docker images
    ```

4. **创建本地映射地址，以便将 mysql 的数据库映射到本地来**

   ```shell
   mkdir /usr/mydocker/mysql/data
   ```

5. **运行 mysql 镜像并创建用户**

   ```shell
   docker run -it --name root -p 3307:3306  -v /usr/docker/mysql/data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123456 -d mysql
   ```

    > 持久化映射并不是必须的，通常对数据库是采用定时备份的方法。

<font size=4 color="DarkViolet">启动 mysql 容器</font>

1. **查看所有的 docker 镜像**

   ```shell
   docker ps -a
   ```

2. **进入mysql镜像**

    ```shell
    docker exec -it [容器id] /bin/bash    
    mysql -uroot -p
    ```

后续命令就和 mysql 的一样了。

#### redis 安装与操作

<font size=4 color="DarkViolet">redis 安装</font>

1. **拉取 redis**

   ```shell
   docker pull redis
   ```

2. **Redis 的初始化**

   ```shell
   # -p 后面是端口，冒号 左边是物理机的端口，右边是对应的 Docker 容器，端口不需要相同。
   
   docker run -it --name redis -p 36379:6379 -d redis
   ```

   初始化完成后，可以通过 `docker ps` 指令查看是否完成了初始化，如果容器已经启动就说明初始化成功。

任何语言，项目使用 redis ，其本质就是向这个 redis 服务器的容器中存储，读取数据。所以这个容器一定开着才能使用 redis 功能。

#### rTorrent-ruTorrent 安装与操作

$~~~~~$ docker 中提供了一个 `rTorrent-ruTorrent` ，可以直接将两个一起安装，直接一起配环境

<font size=4 color="DarkViolet">rTorrent-ruTorrent 安装</font>

1. 拉取镜像

   ```shell
   docker run -dt --name rtorrent-rutorrent -p 20001:80 -p 49160:49160/udp -p 49161:49161 -v /root/down:/downloads diameter/rtorrent-rutorrent:latest
   ```

   - 第一个 `-p` 是将访问端口映射
   - 第二个 `-p` 是将 DHT UDP端口映射（DHT ：基于 BitTorrent 的一个协议）
   - 第三个 `-p` 是数据传入接口
   - `-v /root/down:/downloads` : 将容器内部的 `/downloads` 目录中的内容映射到 `/root/down` 目录中去
   > `/downloads` 该目录下包含：下载文件夹、autodl-irssi配置文件、rtorrent暂存文件(watch/session)、rtorrent和ruTorrent配置文件、nginx和rtorrent日志等
   - `diameter/rtorrent-rutorrent:latest` : 获取类型为 diameter/rtorrent-rutorrent ，版本最新。

2. 进入 ruTorrent

   通过我们设置的访问端口就能直接进入 ruTorrent 的 web 界面 `localhost:20001` 。

> 可以通过开启 BBR 算法来优化速度。

## 附录1：docker的一些指令

<font size=4 color="DarkViolet">docker 命令</font>

```shell
docker stop $(docker ps -a -q)         停止所有容器
docker stop $(docker ps -aq)           停止所有容器

docker rm $(docker ps -a -q)           删除所有容器
docker rm $(docker ps -aq)             删除所有容器
docker rm -f <containerid>             删除指定容器
docker container prune                 删除所有停止的容器

docker ps -a                           查看所有镜像
docker rmi <image id>                  指定id删除镜像
docker rmi $(docker images -q)         删除所有镜像
docker rmi -f $(docker images -q)      强制删除所有镜像

docker image prune --force --all       删除所有不使用的镜像
docker image prune -f -a               删除所有不使用的镜像

docker exec -it ID /bin/bash          进入容器
docker exec -it ID bash               进入容器 

docker stop Name或者ID                停止容器
docker start Name或者ID               启动容器
docker kill Name或者ID                杀死容器
docker restart name或者ID             重启容器

docker exec ：在运行的容器中执行命令
    -d :分离模式: 在后台运行
  -i :即使没有附加也保持 STDIN（标准输入） 打开,以交互模式运行容器，通常与 -t 同时使用；
-t: 为容器重新分配一个伪输入终端，通常与 -i 同时使用，如：
docker exec -it  f94d2c317477 /bin/bash
```

<font size=4 color="DarkViolet">docker 快捷键</font>

```shell
Ctrl + d                     退出并停止容器
Ctrl + p + q                 退出并在后台运行容器；
```
