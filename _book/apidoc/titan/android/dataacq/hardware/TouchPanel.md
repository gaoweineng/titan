# TouchPanel				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

触屏数据采集. 通过DataAcqService.getComponent(TouchPanel.class)获取实例。


## 接口说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(TouchPanel.class)接口获取实例。

> ### getStatus

public ComponentStatus getStatus() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取触屏通信状态。
	
##### 返回值

触屏通信状态。

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
 	TouchPanel touchPanel = dataAcq.getComponent(TouchPanel.class);
	//获取触屏通信状态
    ComponentStatus status = touchPanel.getStatus();
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