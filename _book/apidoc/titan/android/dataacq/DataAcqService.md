# DataAcqService

##### extends titan.android.core.TitanService  #####
				
#### since 1.0.0 ####

## 概览

系统统一接口数据采集服务. 用于获取设备的统计量和状态量. 不能直接实例化DataAcqService，而是通过 TitanContext.getService(Class)接口, 传入参数 DataAcqService.class 获取采集服务代理对象. 

需要采集某一模块的统计量或状态量时，通过getComponent(Class) 接口获取对应模块的实例,入参为模块的类型, 如获取音频孔模块, 传入AudioJack.class, 如果远程采集服务未运行, 则抛出 ServiceDeathException异常. 

## 接口说明

> ### 构造方法

不支持应用直接实例化，而是通过TitanContext.getService(DataAcqService.class)接口获取实例。

> ### getComponent

public <T extends StatsComponent> T getComponent(@NonNull Class<T> clazz) throws ServiceDeathException, ServiceNotFoundException

##### 接口功能
获取采集模块.

##### 方法参数
* clazz：服务代理对象类型，不可为null。枚举类型有：
	- AudioJack.class
	- Battery.class
	- Bluetooth.class
	- Camera.class
	- CPU.class
	- 其他类型...
	
##### 返回值
采集模块实例, 实例类型即为入参clazz指定的类型。

##### 异常
* ServiceNotFoundException： clazz所指模块类型不存在时抛出此异常。
* ServiceDeathException：远程服务未运行时抛出

## 编程示例：

```
TitanContext titan = TitanContext.getTitanContext(context);
 try {
 	DataAcqService dataAcq = titan.getService(DataAcqService.class);
 	AudioJack audioJack = dataAcq.getComponent(AudioJack.class);
 	// 获取音频头插入次数统计量
 	long count = audioJack.getUsage(AudioJack.PLUG_COUNT);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```