# EasyTouchService

##### extends titan.android.core.TitanService  #####
				
#### since 1.0.0 ####

## 概览

系统统一接口以太网服务. 用于查询以太网模块的设置信息. 不能直接实例化EthernetService，而是通过 TitanContext.getService(Class)接口, 传入参数 EthernetService.class 获取采集服务代理对象. 


## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过TitanContext.getService(EthernetService.class)接口获取实例。

> ### isEthernetExist

public boolean isEthernetExist(String iface) throws ServiceDeathException, RemoteExecuteException

##### 功能
检查以太网模块是否存在. 仅检查以太网硬件模块是否存在, 不涉及以太网络是否连接。

##### 参数
* iface：以太网的物理接口名称, 一般为"eth0"。
	
##### 返回值
存在返回true,不存在返回false。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持
	- 参数错误

> ### setEthernetEnabled

public boolean setEthernetEnabled(boolean enabled) throws ServiceDeathException

##### 功能
启用/禁用以太网模块. 仅设置以太网硬件模块, 不涉及以太网络是否连接。

##### 参数
* enabled：启用:true, 禁用:false。

##### 返回值
设置成功返回true,否则返回false。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 系统不支持
	- 设备不支持

> ### isEthernetEnabled

public boolean isEthernetEnabled() throws ServiceDeathException, RemoteExecuteException

##### 功能
检查以太网模块是否启用, 仅检查以太网硬件模块, 不涉及以太网络是否连接。

##### 返回值
启用返回true,禁用返回false。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持

> ### getEthernetIfaceName

public String getEthernetIfaceName() throws ServiceDeathException, RemoteExecuteException

##### 功能
获得以太网的物理接口名称。

##### 返回值
物理接口名称，一般为"eth0"。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持

> ### getEthernetIfaceState

public int getEthernetIfaceState() throws ServiceDeathException, RemoteExecuteException

##### 功能
获得以太网的物理接口的状态。

##### 返回值

物理接口状态值：  

* 0：表示DOWN
* 1：表示UP

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持

> ### getEthernetCarrierState

public int getEthernetCarrierState() throws ServiceDeathException, RemoteExecuteException

##### 功能
获得网线的连接状态。

##### 返回值
当以太网的物理接口状态为UP的时候,即getEthernetIfaceState()返回值为1时 , 读取到的才是准确的，否则返回都是0，返回值有：

- 0:网线未插入
- 1:网线已连接

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持


> ### getEthernetHwaddr

public String getEthernetHwaddr(String iface) throws ServiceDeathException, RemoteExecuteException

##### 功能
获得以太网的物理地址。

##### 参数
* iface：以太网的物理接口名称, 一般为"eth0"。

##### 返回值
以太网物理地址。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持
	- 参数错误

> ### getDHCPInfo

public DHCPInfo getDHCPInfo() throws ServiceDeathException, RemoteExecuteException

##### 功能
获得DHCP信息，应在<b>网络连接成功</b>后调用该接口，才能保证获取到正确的信息。

##### 返回值
DHCP元信息。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 设备不支持

## 编程示例：

```
TitanContext titan = TitanContext.getTitanContext(context);
 try {
 	EthernetService service = titanContext.getService(EthernetService.class);
	boolean exist = service.isEthernetExist("eth0");
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (RemoteExecuteException e) {
	e.printStackTrace();	
 }
```