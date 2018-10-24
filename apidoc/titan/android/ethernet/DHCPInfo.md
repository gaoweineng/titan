# ETShortcutInfo		

##### extends android.os.Parcel  #####
		
#### since 1.0.0 ####

## 概览

悬浮球快捷菜单配置信息。

## 方法说明

> ### getIpAddress

public String getIpAddress()

##### 功能
获取IP地址。

##### 返回值
IP地址(IPv4格式)，获取失败时返回null。

> ### getGateway

public String getGateway()

##### 功能
获取网关。

##### 返回值
网关(IPv4格式)，获取失败时返回null。

> ### getNetmask

public String getNetmask()

##### 功能
获取子网掩码。

##### 返回值
子网掩码(IPv4格式)，获取失败时返回null。

> ### getDns1

public String getDns1()

##### 功能
获取DNS1。

##### 返回值
DNS1(IPv4格式)，获取失败时返回null。

> ### getDns2

public String getDns2()

##### 功能
获取DNS2。

##### 返回值
DNS2(IPv4格式)，获取失败时返回null。

> ### getServerAddress

public String getServerAddress()

##### 功能
获取DHCP服务器地址。

##### 返回值
DHCP服务器地址(IPv4格式)，获取失败时返回null。

> ### getLeaseDuration

public int getLeaseDuration()

##### 功能
获取IP租赁期。

##### 返回值
IP租赁期，单位秒，获取失败时返回 0。