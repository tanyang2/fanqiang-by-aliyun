# fanqiang-by-aliyun
通过阿里云实现0.1元/小时一键翻墙

1.先有一个阿里云账号。。。

2.建立服务器系统镜像，在 香港/日本/新加坡 中选择一个区域，香港最快，以香港为例：

2.1 创建一个临时服务器，选择按量付费模式=》地域选择 香港 =》 推荐 突发性能实例 2核2g =》 Ubuntu 18系统 =》 20GB系统盘 =》 网络按流量计费 推荐 50M带宽

2.2 部署shadowsocks，参见 https://github.com/tanyang2/run-shadowsocks-in-Ubuntu-18

2.3 部署完成=》在本实例磁盘中，创建系统盘快照=》在本实例快照中创建自定义镜像

2.4 释放临时服务器

3.在 云服务器=》香港区域=》部署与弹性=》实例启动模板，创建一个启动模板，选择按量付费=》推荐 突发性能实例 1核1g，20GB系统盘，选择之前的自定义镜像，网络按流量计费 推荐 50M带宽=》登录凭证 新建一个密钥对就行，用不到=》实例名称，推荐："shadowsocks-server"=》保存模板，命名推荐："shadowsocks"

4.创建阿里云api key：在 RAM访问控制 => 新建一个用户，启用编程访问 =》 授予 管理云服务器服务（ECS）的权限，管理云解析（DNS）的权限

5.将配置信息填入，参见 https://github.com/tanyang2/AliyunECSAutoCreate

6.shadowsocks的使用，参见 https://github.com/shadowsocks/shadowsocks-windows

7.推荐使用固定二级域名（需使用阿里云解析），创建服务器并获取到服务器公网ip后，可一键更新域名解析。

如无域名，则将ip配置到shadowsocks client中。
