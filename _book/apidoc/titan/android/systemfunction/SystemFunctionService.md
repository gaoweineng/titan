# SystemFunctionService

##### extends titan.android.core.TitanService  #####
				
#### since 1.0.0 ####

## 概览

SystemFunctionService是一组功能模块的服务代理接口. 不能直接实例化SystemFunctionService，而是通过 TitanContext.getService(Class)接口, 传入参数 SystemFunctionService.class 获取系统功能服务代理对象. 通过getFunction(Class)可以获取包括应用管理，按键管理，位置，存储挂载等功能模块.

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过TitanContext.getService(SystemFunctionService.class)接口获取实例。

> ### getFunction

public <T extends TitanModule<ISystemFunctionService, ?>> T getFunction(Class<T> clazz) throws ServiceDeathException, ServiceNotFoundException

##### 功能
获取功能模块。

##### 参数
* clazz：服务代理对象类型，不可为null。枚举类型有：
	- ApplicationModule.class
	- KeyModule.class
	- LocationModule.class
	- MountModule.class
	- NfcModule.class
	- ProcessModule.class
	- SettingModule.class
	- StatusBarModule.class
	- TelephonyModule
	- UsbModule
	
##### 返回值
功能模块实例, 实例类型即为入参clazz指定的类型。

##### 异常
* ServiceNotFoundException： clazz所指模块类型不存在时抛出此异常。
* ServiceDeathException：远程服务未运行时抛出

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	ApplicationModule application = service.getFunction(ApplicationModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```