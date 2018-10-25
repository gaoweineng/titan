# Camera				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

摄像头数据采集. 通过DataAcqService.getComponent(Camera.class)获取实例。

## 采集常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">getUsage返回类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">FRONT_CAMERA_COUNT</td>
  <td>Long</td>
  <td>获取前置摄像头打开次数</td>
</tr>
<tr>
  <td width="100">BACK_CAMERA_COUNT</td>
  <td>Long</td>
  <td>获取后置摄像头打开次数</td>
</tr>
</table>


## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(Camera.class)接口获取实例。

> ### getUsage

public <T> T getUsage(DataAcqRequest<T> request) throws ServiceDeathException, RemoteExecuteException 

##### 功能
获取采集数据。

##### 参数
* request：采集请求，不可为null。传入[采集常量](#采集常量)：
	- FRONT_CAMERA_COUNT
	- BACK_CAMERA_COUNT
	
##### 返回值
统计量。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getFrontCameraStatus

public ComponentStatus getFrontCameraStatus() throws ServiceDeathException, RemoteExecuteException 

##### 功能

获取前置摄像头状态。
	
##### 返回值

前置摄像头状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getBackCameraStatus

public ComponentStatus getBackCameraStatus() throws ServiceDeathException, RemoteExecuteException 

##### 功能
获取后置摄像头状态。
	
##### 返回值
后置摄像头状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

## 编程示例：

```
TitanContext titan = TitanContext.getTitanContext(context);
 try {
 	DataAcqService dataAcq = titan.getService(DataAcqService.class);
 	Camera camera = dataAcq.getComponent(Camera.class);
	//获取前置摄像头打开次数
 	long count = camera.getUsage(Camera.FRONT_CAMERA_COUNT);
 	// 获取前置摄像头状态
    ComponentStatus status = camera.getFrontCameraStatus();
    //状态码等级
    Level level = status.getLevel();
    //状态码
    String statusCode = status.getStatusCode();
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 } catch (RemoteExecuteException e) {
 	e.printStackTrace();
 }
```