# Printer				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

打印设备数据采集. 通过DataAcqService.getComponent(Printer.class)获取实例。

## 采集常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">getUsage返回类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">HEAT_TEMP_COUNT</td>
  <td>Long</td>
  <td>获取打印高温次数</td>
</tr>
<tr>
  <td width="100">LOW_TEMP_COUNT</td>
  <td>Long</td>
  <td>获取打印低温次数</td>
</tr>
<tr>
  <td width="100">FEED_COUNT</td>
  <td>Long</td>
  <td>获取走纸电机步进量</td>
</tr>
<tr>
  <td width="100">PRINTER_MODEL</td>
  <td>String</td>
  <td>获取打印机芯型号</td>
</tr>
<tr>
  <td width="100">PRINTER_PAPER_LENGTH</td>
  <td>Long</td>
  <td>获取打印走纸长度(毫米)</td>
</tr>
</table>


## 接口说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(Printer.class)接口获取实例。

> ### getUsage

public <T> T getUsage(DataAcqRequest<T> request) throws ServiceDeathException, RemoteExecuteException 

##### 接口功能
获取采集数据。

##### 方法参数
* request：采集请求，不可为null。传入[采集常量](#采集常量)：
	- HEAT_TEMP_COUNT
	- LOW_TEMP_COUNT
	- FEED_COUNT
	- PRINTER_MODEL
	- PRINTER_PAPER_LENGTH
	
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

获取打印设备状态。
	
##### 返回值

打印设备状态。

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
 	Printer printer = dataAcq.getComponent(Printer.class);
	//获取打印高温次数
 	long count = printer.getUsage(Printer.HEAT_TEMP_COUNT);
 	//获取打印设备状态
    ComponentStatus status = printer.getStatus();
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