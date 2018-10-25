# StatusBarModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

状态栏管理模块.对物理按键如电源键及虚拟按键的管理接口. 通过SystemFunctionService.getFunction(StatusBarModule.class)获取实例。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(StatusBarModule.class)接口获取实例。

> ### isPanelExpandEnabled

public boolean isPanelExpandEnabled() throws ServiceDeathException, RemoteExecuteException

##### 功能
检查状态栏下拉是否启用。

##### 返回值
状态栏下拉启用返回true, 否则返回false
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setPanelExpandEnabled

public boolean setPanelExpandEnabled(boolean enabled) throws ServiceDeathException

##### 功能
设置状态栏下拉是否启用。

##### 参数
* enabled：启用下拉为true, 禁用下拉为false。

##### 返回值  
设置成功返回true, 否则返回false.返回false时可通过 TitanContext.getLastError()获取错误码。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	StatusBarModule statusBar = service.getFunction(StatusBarModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```