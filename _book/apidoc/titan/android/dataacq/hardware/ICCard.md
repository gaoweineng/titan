# ICCard				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

接触式卡模块数据采集. 通过DataAcqService.getComponent(ICCard.class)获取实例。

## 采集常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">getUsage返回类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">POWERUP_SUCCESS_COUNT</td>
  <td>Long</td>
  <td>获取IC卡上电成功次数</td>
</tr>
<tr>
  <td width="100">POWERUP_FAIL_COUNT</td>
  <td>Long</td>
  <td>获取IC卡上电失败次数</td>
</tr>
<tr>
  <td width="100">APDU_FAIL_COUNT</td>
  <td>Long</td>
  <td>获取IC卡APDU失败次数</td>
</tr>
</table>


## 接口说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(ICCard.class)接口获取实例。

> ### getUsage

public <T> T getUsage(DataAcqRequest<T> request) throws ServiceDeathException, RemoteExecuteException 

##### 接口功能
获取采集数据.

##### 方法参数
* request：采集请求，不可为null。传入[采集常量](#采集常量)：
	- POWERUP_SUCCESS_COUNT
	- POWERUP_FAIL_COUNT
	- APDU_FAIL_COUNT
		
##### 返回值
统计量。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限时
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getICCard1Status

public ComponentStatus getICCard1Status() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取IC卡设备状态。
	
##### 返回值

IC卡设备状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getICCard2Status

public ComponentStatus getICCard2Status() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取IC卡2设备状态。
	
##### 返回值

IC卡2设备状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getSAM1CardStatus

public ComponentStatus getSAM1CardStatus() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取SAM1设备状态。
	
##### 返回值

SAM1设备状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getSAM2CardStatus

public ComponentStatus getSAM2CardStatus() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取SAM2设备状态。
	
##### 返回值

SAM2设备状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getSAM3CardStatus

public ComponentStatus getSAM3CardStatus() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取SAM3设备状态。
	
##### 返回值

SAM3设备状态。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

> ### getSAM4CardStatus

public ComponentStatus getSAM4CardStatus() throws ServiceDeathException, RemoteExecuteException 

##### 接口功能

获取SAM4设备状态。
	
##### 返回值

SAM4设备状态。

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
 	ICCard iccard = dataAcq.getComponent(ICCard.class);
	//获取IC卡上电成功次数
 	long count = iccard.getUsage(ICCard.POWERUP_SUCCESS_COUNT);
 	//获取ICCard设备1状态
    ComponentStatus status = iccard.getICCard1Status();
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