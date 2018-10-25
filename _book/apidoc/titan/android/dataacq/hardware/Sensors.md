# Sensors				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

传感器数据采集. 通过DataAcqService.getComponent(Sensors.class)获取实例。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(Sensors.class)接口获取实例。

> ### getLightSensorStatus

public ComponentStatus getLightSensorStatus() throws ServiceDeathException, RemoteExecuteException 

##### 功能

获取光传感器通信状态。
	
##### 返回值

光传感器通信状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getAccSensorStatus

public ComponentStatus getAccSensorStatus() throws ServiceDeathException, RemoteExecuteException 

##### 功能

获取加速传感器通信状态。
	
##### 返回值

加速传感器通信状态。

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
 	Sensors sensors = dataAcq.getComponent(Sensors.class);
	//获取打印设备状态
    ComponentStatus status = sensors.getLightSensorStatus();
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