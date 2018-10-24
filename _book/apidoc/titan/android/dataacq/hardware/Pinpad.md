# Pinpad				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

Pinpad模块数据采集. 通过DataAcqService.getComponent(Pinpad.class)获取实例。

## 采集常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">getUsage返回类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">OFFLINE_COUNT</td>
  <td>Long</td>
  <td>获取脱机PIN输入次数</td>
</tr>
<tr>
  <td width="100">ONLINE_COUNT</td>
  <td>Long</td>
  <td>获取联机PIN输入次数</td>
</tr>
<tr>
  <td width="100">NOPIN_COUNT</td>
  <td>Long</td>
  <td>获取非PIN输入次数</td>
</tr>
</table>


## 接口说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(Battery.class)接口获取实例。

> ### getUsage

public <T> T getUsage(DataAcqRequest<T> request) throws ServiceDeathException, RemoteExecuteException 

##### 接口功能
获取采集数据。

##### 方法参数
* request：采集请求，不可为null。传入[采集常量](#采集常量)：
	- OFFLINE_COUNT
	- ONLINE_COUNT
	- NOPIN_COUNT
	
##### 返回值
统计量。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限时
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getStatus

public ComponentStatus getStatus() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取密码键盘状态。
	
##### 返回值

密码键盘状态。

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
 	Pinpad pinpad = dataAcq.getComponent(Pinpad.class);
	//获取联机PIN输入次数
 	long count = pinpad.getUsage(Pinpad.ONLINE_COUNT);
 	//获取密码键盘状态
    ComponentStatus status = pinpad.getStatus();
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