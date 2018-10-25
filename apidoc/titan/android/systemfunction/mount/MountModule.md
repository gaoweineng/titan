# MountModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

外置存储设备挂载模块管理类. 通过SystemFunctionService.getFunction(MountModule.class)获取实例。

## 接口类 

### interface StorageEventListener

存储器事件监听器, 用于监听存储器挂载/解除挂载事件。

> #### onUsbMassStorageConnectionChanged

public void onUsbMassStorageConnectionChanged(boolean connected)

##### 功能
当检测到USB大容量存储器的状态发生变化时回调。

##### 参数
* connected：USB大容量存储器已经连接上时为true, 否则为false。

> #### onStorageStateChanged

public void onStorageStateChanged(String path, String oldState, String newState)

##### 功能
存储器状态改变时回调。

##### 参数
* path：存储器文件系统路径。
* oldState：存储器之前的状态, 状态码与android.os.Environment.getExternalStorageState()一致。
* newState:存储器当前的状态, 状态码与android.os.Environment.getExternalStorageState()一致。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(MountModule.class)接口获取实例。

> ### mountSDcard

public void mountSDcard() throws ServiceDeathException, RemoteExecuteException

##### 功能
挂载sdcard存储器. 挂载和解除挂载存储器是一个异步过程, 如果应用需要获得存储器状态的反馈, 可以通过注册监听器 registerStorageEventListener(StorageEventListener)进行结果监听。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 系统不支持

> ### mountUdisk

public void mountUdisk() throws ServiceDeathException, RemoteExecuteException

##### 功能
挂载U盘. 挂载和解除挂载存储器是一个异步过程, 如果应用需要获得存储器状态的反馈, 可以通过注册监听器 registerStorageEventListener(StorageEventListener)进行结果监听。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 系统不支持

> ### unmountSDcard

public void unmountSDcard() throws ServiceDeathException, RemoteExecuteException

##### 功能
解除挂载sdcard存储器. 挂载和解除挂载存储器是一个异步过程, 如果应用需要获得存储器状态的反馈, 可以通过注册监听器 registerStorageEventListener(StorageEventListener)进行结果监听。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 系统不支持

> ### unmountUdisk

public void unmountUdisk() throws ServiceDeathException, RemoteExecuteException

##### 功能
解除挂载U盘. 挂载和解除挂载存储器是一个异步过程, 如果应用需要获得存储器状态的反馈, 可以通过注册监听器 registerStorageEventListener(StorageEventListener)进行结果监听。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 系统不支持

> ### registerStorageEventListener

public boolean registerStorageEventListener(StorageEventListener listener) throws ServiceDeathException

##### 功能
注册一个全局的存储器事件监听器, 用于接收存储器挂载状态改变时的异步通知.
由于挂载是一个异步过程, 应用应该在调用挂载mountSDcard(), mountUdisk()或解除挂载 unmountSDcard(), unmountUdisk()方法调用前注册监听器, 在挂载状态改变时接收事件通知. 当应用不再需要监听存储器事件时需要调用 unregisterStorageEventListener()方法取消监听, 否则如果有其他线程或其他应用操作存储器时, 应用仍能接收到事件通知。

##### 参数
* listener：存储器事件监听器。

##### 返回值  
注册成功返回true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### unregisterStorageEventListener

public boolean unregisterStorageEventListener() throws ServiceDeathException

##### 功能
反注册一个全局的存储器事件监听器，当应用不再需要监听存储器事件时需要取消监听, 否则如果有其他线程或其他应用操作存储器时, 应用仍能接收到事件通知。

##### 返回值  
反注册成功返回true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。


## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	MountModule mount = service.getFunction(MountModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```