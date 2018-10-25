# ResetFactoryService

##### extends titan.android.core.TitanService  #####
				
#### since 1.0.0 ####

## 概览

恢复出厂设置工具类. 不能直接实例化ResetFactoryService，而是通过 TitanContext.getService(Class)接口, 传入参数 ResetFactoryService.class 获取恢复出厂设置服务代理对象。 

## 接口类 

### interface ResetListener

恢复出厂设置结果回调。

> #### onResult

public void onResult(int result)

##### 功能
恢复出厂设置过程及结果回调。

##### 参数
* result：恢复出厂设置回调结果代码。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过TitanContext.getService(ResetFactoryService.class)接口获取实例。

> ### resetDeep

public void resetDeep(boolean clean, ResetListener listener) throws ServiceDeathException, RemoteExecuteException

##### 功能
深度恢复出厂设置，包括卸载全部非系统应用、清理（sdcard、cache、系统）数据、重新安装客户预装应用。

##### 参数
* clean：是否选择清理系统数据, true表示清理, false表示不清理。
* listener：恢复出厂设置结果回调
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 系统不支持
	- 参数错误

> ### resetShallow

public void resetShallow(ResetListener listener) throws ServiceDeathException, RemoteExecuteException

##### 功能
浅度恢复出厂设置，只卸载非系统的第三方应用（不会卸载客户的预装应用）。

##### 参数
* listener：恢复出厂设置结果回调。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 系统不支持
	- 参数错误

## 编程示例：

```
TitanContext titan = TitanContext.getTitanContext(context);
 try {
 	ResetFactoryService service = titan.getService(ResetFactoryService.class);
 	//深度恢复出厂设置
 	service.resetDeep(true, new ResetListener(){
		@Override
		public void onResult(int result){
		}
	});
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 } catch (RemoteExecuteException e) {
 	e.printStackTrace();
 }
```