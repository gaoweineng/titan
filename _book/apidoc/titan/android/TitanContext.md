# TitanContext		

##### Singleton Pattern #####
##### since 1.0.0 #####

## 概览  

系统统一接口上下文，应用程序使用系统统一接口服务的全局接口。通过TitanContext可以访问：

- [DataAcqService 数据采集](DataAcqService.md)
- [EasyTouchService 悬浮球](EashTouchService.md)
- [EthernetService 以太网](EthernetService.md)
- [ResetFactoryService 恢复出厂设置](ResetFactoryService.md)
- [SystemFunctionService 系统功能](SystemFunctionService.md)

等系统功能。

## 接口说明

> ### 构造方法

单例模式，不支持应用直接实例化，而是通过getContext(Context)接口获取实例。

> ### getTitanContext

public static TitanContext getTitanContext(Context context)	

##### 接口功能
获取TitanContext实例。

##### 方法参数
* context：应用上下文。

##### 返回值
TitanContext唯一实例。

> ### getService

public <T extends TitanService> T getService(@NonNull Class<T> serviceType) throws ServiceNotFoundException

##### 接口功能
获取统一接口远程服务在应用端的代理对象,通过服务代理对象访问系统功能。

##### 方法参数
* serviceType：服务代理对象类型，不可为null。枚举类型有：
	- DataAcqService.class
	- EasyTouchService.class
	- EthernetService.class
	- ResetFactoryService.class
	- SystemFunctionService.class

##### 返回值
服务代理对象，由入参serviceType指定代理对象类型。

##### 异常
* ServiceNotFoundException： serviceType所指类型服务不存在时抛出此异常。


## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context); 
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	ApplicationModule application = service.getFunction(ApplicationModule.class);
 	AppSignInfo appSignInfo = application.getAppSignInfo("com.example.demo");
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 } catch (RemoteExecuteException e) {
 	e.printStackTrace();
 }
```
    
    
