> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

本系统一共管理员，用户角色。

主要功能：收货地址管理、经验交流平台管理、公告信息管理、跳蚤市场管理、商品留言管理、商品订单管理、用户管理

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：SpringBoot + MyBatis + Vue + Bootstrap + jQuery

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码地址：[http://www.codegym.top](http://wwww.codegym.top/)


# 运行截图

## 文档截图



### 项目截图

![图片1](https://i-blog.csdnimg.cn/img_convert/9c69115d4b8ae697ee823cd2c152e08c.png)

![图片2](https://i-blog.csdnimg.cn/img_convert/54ac7b9f7a515fba0d2e68565918516f.png)

![图片3](https://i-blog.csdnimg.cn/img_convert/7db914fb4ba9dcc63568e2925ea8a6cd.png)
### 代码

```

        if (RequestUtils.isAdministrator()){
            Long distinctDeviceCount = deviceOrganizationQryExe.getDistinctDeviceCount();
            Long todayIncreaseDeviceCount = deviceOrganizationQryExe.getTodayIncreaseDeviceCount();
            deviceResources.setTotalDeviceCount(distinctDeviceCount.intValue());
            deviceResources.setTodayIncreaseDeviceCount(todayIncreaseDeviceCount.intValue());
        }else{
     
            List<DeviceDO> devicesActiveStatus = deviceServiceGateway.getDevicesActiveStatus();
            Integer totalDeviceCount = devicesActiveStatus.size();
            if (CollectionUtils.isNotEmpty(devicesActiveStatus)){
                Integer offDeviceCount = (int)devicesActiveStatus.stream().filter(item -> item.getActiveFlag().equals("false")).count();
                Integer onlineDeviceCount = (int)devicesActiveStatus.stream().filter(item -> item.getActiveFlag().equals("true")).count();
                deviceResources.setOnlineDeviceCount(onlineDeviceCount);
                deviceResources.setOfflineDeviceCount(offDeviceCount);
            }else {
                deviceResources.setOnlineDeviceCount(0);
                deviceResources.setOfflineDeviceCount(0);
            }
            deviceResources.setTotalDeviceCount(totalDeviceCount);
        }
```
