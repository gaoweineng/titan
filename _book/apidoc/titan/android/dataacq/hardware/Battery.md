# Battery				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

电池数据采集. 通过DataAcqService.getComponent(Battery.class)获取实例。

## 采集常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">getUsage返回类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">POWER_LEVEL</td>
  <td>String</td>
  <td>获取电池电量</td>
</tr>
<tr>
  <td width="100">BATTERY_VOLTAGE</td>
  <td>String</td>
  <td>获取电池电压</td>
</tr>
<tr>
  <td width="100">STANDBY_BATTERY_VOLTAGE</td>
  <td>String</td>
  <td>获取备份电池电压</td>
</tr>
<tr>
  <td width="100">CHARGE_DURATION</td>
  <td>Long</td>
  <td>获取充电累计时间(分钟)</td>
</tr>
<tr>
  <td width="100">POWER_USAGE</td>
  <td>String</td>
  <td>获取电量使用情况(mAh)</td>
</tr>
<tr>
  <td width="100">CHARGE_COUNT</td>
  <td>Long</td>
  <td>获取充电次数</td>
</tr>
</table>


## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(Battery.class)接口获取实例。

> ### getUsage

public <T> T getUsage(DataAcqRequest<T> request) throws ServiceDeathException, RemoteExecuteException 

##### 功能

获取采集数据。

##### 参数

* request：采集请求，不可为null。传入[采集常量](#采集常量)：
	- POWER_LEVEL
	- BATTERY_VOLTAGE
	- STANDBY_BATTERY_VOLTAGE
	- CHARGE_DURATION
	- POWER_USAGE
	- CHARGE_COUNT
	
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

##### 功能

获取电池状态量信息。
	
##### 返回值

电池状态量信息。

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
 	Battery battery = dataAcq.getComponent(Battery.class);
	//获取充电累计时间(分钟)
 	long count = battery.getUsage(Battery.CHARGE_DURATION);
 	//获取电池电压
    String voltage = battery.getUsage(Battery.BATTERY_VOLTAGE);
	//获取电池状态
    ComponentStatus status = battery.getStatus();
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