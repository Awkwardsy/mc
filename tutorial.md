## Java准备
1.16.5 以下: java8
1.16.5 以上: java17
在azul网站上下载zulu版本的java
解压后拷贝到/opt下, 需要sudo权限
```
sudo update-alternatives --install /usr/bin/java java "java的二进制文件地址" 300
```
测试java是否工作正常:
```
yhh@yhhserver:~$ java --version
java 17.0.7 2023-05-27 LTS
Java Runtime Environment Zing23.05.0.0+2 (build 17.0.7+7-LTS)
Zing 64-Bit Tiered VM Zing23.05.0.0+2 (build 17.0.7-zing_23.05.0.0-b2-product-linux-X86_64, mixed mode)
```

## Fabric 服务端安装

官网下载Fabric installer jar文件 按照指引安装(https://fabricmc.net/wiki/zh_cn:player:tutorials:install_server)

```
# 运行 Fabric Installer
java -jar installer.jar server -mcversion 1.19.2 -downloadMinecraft
 
# 删除 Fabric Installer
rm installer.jar
 
# 重命名 Jar 文件
mv server.jar vanilla.jar
mv fabric-server-launch.jar server.jar
echo "serverJar=vanilla.jar" > fabric-server-launcher.properties
 
# 启动 Minecarft 服务器
java -jar server.jar
```
最后一步启动会失败, 需要同意ELUA协议, 此时不需要再启动了, 可以添加mod了和修改设置了

## Fabric 服务器设置

*server.properties*修改
```
online-mode=false
pvp=false
level-seed=20230613
view-distance=6
simulation-distance=6
```

## 添加Mod

优化:
```DFU载入优化 lazydfu
禁用聊天举报 NoChatReport
氪 Krypton
锂 Lithium
平滑区块保存 smoothchunk
铁氧体磁芯 Ferritecore
星光 starlight
Bug修复 Debugify
内存泄漏修复 memoryleakfix
```

辅助:
```
地毯 carpet
REI物品管理 RoughlyEnoughItems
Textile备份 textile backup
连锁挖掘 Diggusmaximus
苹果皮 appleskin
树叶速腐 leafdecay
玉 jade
简单收获 harvestwithease
地图 Xaeros minimap/worldmap
```


## 启动服务器
```
java -jar server.jar 
# 在可以稳定之后加上nogui参数

# 优化的开服参数
java -server -Xms8g -Xmx8g -XX:+AggressiveOpts -XX:+UseFastAccessorMethods -XX:+UseG1GC -XX:SurvivorRatio=6 -XX:G1ReservePercent=15 -XX:ParallelGCThreads=2 -XX:ConcGCThreads=1 -XX:InitiatingHeapOccupancyPercent=40 -jar server.jar nogui
```

## 参考链接
```
https://www.mcadmin.cn/
https://mhy278.gitee.io/minecraftserverhostguidehtml/
```

