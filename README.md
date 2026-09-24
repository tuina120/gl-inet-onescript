# GL-iNet 系列路由器 一键iStoreOS风格化脚本
[![GitHub](https://img.shields.io/github/license/wukongdaily/gl-inet-onescript.svg?label=LICENSE&logo=github&logoColor=%20)](https://github.com/wukongdaily/gl-inet-onescript/blob/master/LICENSE)
![GitHub Stars](https://img.shields.io/github/stars/wukongdaily/gl-inet-onescript.svg?style=flat&logo=appveyor&label=Stars&logo=github)
![GitHub Forks](https://img.shields.io/github/forks/wukongdaily/gl-inet-onescript.svg?style=flat&logo=appveyor&label=Forks&logo=github)



## 🤔 这是什么？

该项目可以让MT2500/MT3000/MT6000路由器在不刷机情况下,一键变成iStoreOS风格。<br><br>
<img alt="Static Badge" src="https://img.shields.io/badge/MT6000-0?style=flat-square&logoColor=8A2BE2&label=%E5%9E%8B%E5%8F%B7&labelColor=000000&color=336666">
<img alt="Static Badge" src="https://img.shields.io/badge/MT2500A-0?style=flat-square&logoColor=8A2BE2&label=%E5%9E%8B%E5%8F%B7&labelColor=000000&color=D94600"> 
<img alt="Static Badge" src="https://img.shields.io/badge/MT3000-0?style=flat-square&logoColor=8A2BE2&label=%E5%9E%8B%E5%8F%B7&labelColor=000000&color=2828FF"> 
## 💡 特色功能

- 💻 支持`一键安装iStoreOS风格`
- 💻 支持`一键安装紫色的Argon主题`
- 💻 支持`一键安装文件管理器`
- 🔑 支持`一键设置MT-3000风扇开始工作的温度`
- 🌏 支持`一键部署Docker运行环境`
- 🌏 支持`一键安装docker-compose`
- 🐋 支持`一键安装GL原厂adguardhome`
- 📕 支持`一键恢复原厂的OPKG软件源`
- 🔑 支持`MT-3000 一键更换分区到U盘`
- 💡 使用条件：GL-iNet 原厂固件（非测试版、预览版）
- GL-inet MT-6000✅
- GL-inet MT-3000 ✅
- GL-inet MT-2500 ✅ 固件版本4.5.0（最好降级到此版本）
- OrangePi Zero3(官方Openwrt镜像)


## 🚀 快速上手

### 1. SSH连接到路由器,或者在路由器终端执行如下命令

```bash
wget -O gl-inet.sh https://cafe.cpolar.cn/wkdaily/gl-inet-onescript/raw/branch/master/gl-inet.sh && chmod +x gl-inet.sh && ./gl-inet.sh
```

### 下次如何调用,在当前目录下执行
```bash
sh gl-inet.sh
```

### 2.单独安装Docker
```bash
wget -O do_docker.sh https://cafe.cpolar.cn/wkdaily/gl-inet-onescript/raw/branch/master/docker/do_docker.sh && chmod +x do_docker.sh && ./do_docker.sh
```


### 3.单独安装iStore商店
```bash
wget -O /tmp/reinstall_istore.sh https://gitee.com/wukongdaily/gl_onescript/raw/master/reinstall_istore.sh && chmod +x /tmp/reinstall_istore.sh && /tmp/reinstall_istore.sh

```

### 4.单独安装文件管理器
```bash
wget -O /tmp/reinstall_istore.sh https://gitee.com/wukongdaily/gl_onescript/raw/master/reinstall_istore.sh && chmod +x /tmp/reinstall_istore.sh && /tmp/reinstall_istore.sh
/tmp/is-opkg install app-meta-linkease

```


### 5.新手ssh连接注意事项
https://github.com/wukongdaily/HowToUseSSH
### 6.使用独立版docker-compose
```bash
docker-compose version
```
```bash
# 注意上述代码中使用的是独立版docker-compose，并非标准安装的docker compose
# 区别就是中间没有空格是一个独立的可执行文件。当然这个叫做docker-compose的可执行文件，
# 你可以任意命名，不过就是习惯这样写，还有的人重命名为docker_compose之类的都可以。
```

### 辅助视频教程⬇️
https://www.bilibili.com/video/BV1YJ4m1L7A3/
### 博客地址:https://wkdaily.cpolar.cn
# Docker面板的选择
## 🔑 安装1panel 面板 来管理Docker 容器

### 可以使用 docker离线包加载
```bash
国内地址 https://pan.baidu.com/s/1Zh913sP6rZWXmhC_rKjWQA?pwd=1111

备选地址 https://drive.google.com/drive/folders/15HL-lHxW9J74Fwwebrg0lMjRsenScWnO
```
### 上传到U盘其他空间(这里注意是/mnt/upan_data)
```bash
docker load < /mnt/upan_data/1panel-arm64.tar.gz
```

```bash
docker run -d \
    --name 1panel \
    --restart always \
    --network host \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /www/data/1panel-data:/mnt/data_sda2/1panel_data \
    -e TZ=Asia/Shanghai \
    moelin/1panel:latest
```
`其中 /mnt/data_sda2/ 可以换成自己实际的路径,最好是空间大点的`
- 默认端口：10086
- 默认账户：1panel
- 默认密码：1panel_password
- 默认入口：entrance

## 访问地址
```bash
http://192.168.8.1:10086/entrance
```

## 🔑 安装Fast OS面板 来管理Docker 容器
```bash
docker run -d \
--name fastos \
--restart always \
-p 8081:8081 \
-p 8082:8082 \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /etc/docker/:/etc/docker/ \
-v /root/data:/fast/data \
-e FAST_STORE=http://dockernb.com:8300 \
wangbinxingkong/fast:latest
```
### Fast OS 面板离线包
```bash
https://pan.baidu.com/s/1S5jxahCzE-HyIa-mUvOcZQ?pwd=1111
```
  
## 🗂️ 引用项目

本项目的开发参照了以下项目，感谢这些开源项目的作者：
### istore
https://github.com/linkease/istore

![mt3000](https://github.com/wukongdaily/gl-inet-onescript/assets/143675923/0ff6cb12-0812-4198-b97b-30698da6a8c4)

# 其他docker举例 盒子助手docker版
```bash
docker run -d \
  --restart unless-stopped \
  --name tvhelper \
  -p 2299:22 \
  -p 2288:80 \
  -v "/mnt/upan_data/tvhelper_data:/tvhelper/shells/data" \
  -e PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib/android-sdk/platform-tools \
  wukongdaily/box:latest
```
# 常见问题
- 1、如果你发现运行容器后,访问docker容器的web界面之后，路由器的指示灯发生闪烁，不用慌，其实没有断网。
  wan口网线拔了再插上就好了。其实不处理也无所谓的。闪烁也不代表没有网络。不准确的。
- 2、如果你发现运行容器后,访问不了docker容器的web界面。一般重启路由器就能解决。
- 3、请注意为了节省路由器空间,平时上传文件 最好是上传到 /mnt/upan_data 这个目录下。因为这是U盘空间，比较大。
# 特别说明
```
对于MT2500和MT3000 如果你打算安装使用docker，建议使用的固件版本4.5.0，在这之后的版本目前测试发现不太稳定，不太适合docker。
4.5.0 固件可以从官网下载。这个路由器可以随时降级到4.5.0的。
https://dl.gl-inet.cn/release/router/stable/mt3000/4.5.0
https://dl.gl-inet.cn/release/router/stable/mt2500/4.5.0
```
# 💰打赏作者💰
<img src="https://github.com/wukongdaily/tvhelper-docker/assets/143675923/1f92c5ba-1b6b-4967-a1ab-20697159badc" width="30%" />
                                                                                                                                                                                                                                                                                                                                                                                                    
wget -O gl-inet.sh https://cdn.jsdelivr.net/gh/tuina120/gl-inet-onescript@master/gl-inet.sh && sed -i 's|https://cafe.cpolar.cn/wkdaily/gl-inet-onescript/raw/branch/master/|https://cdn.jsdelivr.net/gh/tuina120/gl-inet-onescript@master/|g' gl-inet.sh && chmod +x gl-inet.sh && ./gl-inet.sh
