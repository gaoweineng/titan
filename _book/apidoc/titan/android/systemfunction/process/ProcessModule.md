# ProcessModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

应用进程模块管理类。 通过SystemFunctionService.getFunction(ProcessModule.class)获取实例。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(ProcessModule.class)接口获取实例。

> ### clearRecentTasks

public boolean clearRecentTasks() throws ServiceDeathException

##### 功能
清空杀死同一用户最近启动的后台任务. 远端服务限制一次清空任务最大个数为100, 如果后台任务个数大于100, 需要再次执行此方法, 直到清空干净.错误码可通过TitanContext.getLastError()查询。

##### 返回值
成功清空任务返回true, 否则返回false
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	ProcessModule process = service.getFunction(ProcessModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```