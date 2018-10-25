# SystemUsage				

##### extends titan.android.core.dadaacq.StatsComponent #####

#### since 1.0.0 ####

## 概览

系统信息数据采集. 通过DataAcqService.getComponent(SystemUsage.class)获取实例。

## 采集常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">getUsage返回类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">POWERON_COUNT</td>
  <td>Long</td>
  <td>获取开机次数</td>
</tr>
<tr>
  <td width="100">SHUTDOWN_COUNT</td>
  <td>Long</td>
  <td>获取关机次数</td>
</tr>
<tr>
  <td width="100">LIFECYCLE_TOTAL</td>
  <td>Long</td>
  <td>获取累计运行时间(分钟)</td>
</tr>
<tr>
  <td width="100">PRODUCT_NAME</td>
  <td>String</td>
  <td>获取品牌名称</td>
</tr>
<tr>
  <td width="100">MODEL_NAME</td>
  <td>String</td>
  <td>获取型号</td>
</tr>
<tr>
  <td width="100">DEVICE_NAME</td>
  <td>String</td>
  <td>获取设备名称</td>
</tr>
<tr>
  <td width="100">SDCARD_TOTAL</td>
  <td>Long</td>
  <td>获取内置SD卡容量(bytes)</td>
</tr>
<tr>
  <td width="100">SDCARD_AVAILABLE</td>
  <td>Long</td>
  <td>获取内置SD卡可用大小(bytes)</td>
</tr>
<tr>
  <td width="100">NET_TYPE</td>
  <td>String</td>
  <td>获取网络类型</td>
</tr>
<tr>
  <td width="100">SDK_VERSION</td>
  <td>String</td>
  <td>获取SDK版本</td>
</tr>
<tr>
  <td width="100">ANDROID_VERSION</td>
  <td>String</td>
  <td>获取Android版本</td>
</tr>
<tr>
  <td width="100">UPTIME_INFO</td>
  <td>Long</td>
  <td>获取系统运行时间(分钟)</td>
</tr>
<tr>
  <td width="100">BASEBAND_VERSION</td>
  <td>String</td>
  <td>获取基带版本</td>
</tr>
<tr>
  <td width="100">SYSTEM_VERSION</td>
  <td>String</td>
  <td>获取系统版本</td>
</tr>
<tr>
  <td width="100">SMARTOS_VERSION</td>
  <td>String</td>
  <td>获取SmartOS版本</td>
</tr>
<tr>
  <td width="100">MEMORY_TOTAL</td>
  <td>Long</td>
  <td>获取系统总内存大小(bytes)</td>
</tr>
<tr>
  <td width="100">MEMORY_AVAILABLE</td>
  <td>Long</td>
  <td>获取系统可用内存大小(bytes)</td>
</tr>
<tr>
  <td width="100">DEVICE_MANUFACTURER</td>
  <td>String</td>
  <td>获取厂商名称</td>
</tr>
<tr>
  <td width="100">SERIAL_NO</td>
  <td>String</td>
  <td>获取序列号</td>
</tr>
<tr>
  <td width="100">IMEI</td>
  <td>String</td>
  <td>获取IMEI号</td>
</tr>
<tr>
  <td width="100">MEID</td>
  <td>String</td>
  <td>获取MEID号</td>
</tr>
<tr>
  <td width="100">SAFE_PATCH_VERSION</td>
  <td>String</td>
  <td>获取安全补丁版本</td>
</tr>
<tr>
  <td width="100">KERNEL_VERSION</td>
  <td>String</td>
  <td>获取内核版本号</td>
</tr>
<tr>
  <td width="100">ROM_TOTAL</td>
  <td>Long</td>
  <td>获取机身存储容量(bytes)</td>
</tr>
<tr>
  <td width="100">ROM_AVAILABLE</td>
  <td>Long</td>
  <td>获取机身存储可用大小(bytes)</td>
</tr>
<tr>
  <td width="100">TFCARD_TOTAL</td>
  <td>Long</td>
  <td>获取TF卡容量(bytes)</td>
</tr>
<tr>
  <td width="100">TFCARD_AVAILABLE</td>
  <td>Long</td>
  <td>获取TF卡可用大小(bytes)</td>
</tr>
<tr>
  <td width="100">IP_ADDRESS</td>
  <td>String</td>
  <td>获取IP地址</td>
</tr>
<tr>
  <td width="100">BOOT_VERSION</td>
  <td>String</td>
  <td>获取Boot版本</td>
</tr>
<tr>
  <td width="100">SDCARD_STATUS</td>
  <td>String</td>
  <td>获取内置SD卡状态</td>
</tr>
<tr>
  <td width="100">TFCARD_STATUS</td>
  <td>String</td>
  <td>获取TF卡状态</td>
</tr>
</table>


## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过DataAcqService.getComponent(SystemUsage.class)接口获取实例。

> ### getUsage

public <T> T getUsage(DataAcqRequest<T> request) throws ServiceDeathException, RemoteExecuteException 

##### 功能
获取采集数据。

##### 参数
* request：采集请求，不可为null。传入[采集常量](#采集常量)：
	- POWERON_COUNT
	- SHUTDOWN_COUNT
	- LIFECYCLE_TOTAL
	- PRODUCT_NAME
	- MODEL_NAME
	- DEVICE_NAME
	- SDCARD_TOTAL
	- SDCARD_AVAILABLE
	- NET_TYPE
	- SDK_VERSION
	- ANDROID_VERSION
	- UPTIME_INFO
	- BASEBAND_VERSION
	- SYSTEM_VERSION
	- SMARTOS_VERSION
	- MEMORY_TOTAL
	- MEMORY_AVAILABLE
	- DEVICE_MANUFACTURER
	- SERIAL_NO
	- IMEI
	- MEID
	- SAFE_PATCH_VERSION
	- KERNEL_VERSION
	- ROM_TOTAL
	- ROM_AVAILABLE
	- TFCARD_TOTAL
	- TFCARD_AVAILABLE
	- IP_ADDRESS
	- BOOT_VERSION
	- SDCARD_STATUS
	- TFCARD_STATUS
	
##### 返回值
统计量。

##### 异常
* ServiceDeathException 远程服务未运行时抛出。
* RemoteExecuteException 以下错误时抛出：
	* 应用无权限时
	* 数据解析失败
	* 采集因子不被支持
	* 系统不支持

## 编程示例：

```
TitanContext titan = TitanContext.getTitanContext(context);
 try {
 	DataAcqService dataAcq = titan.getService(DataAcqService.class);
 	SystemUsage systemUsage = dataAcq.getComponent(SystemUsage.class);
	//获取开机次数
 	long count = systemUsage.getUsage(SystemUsage.POWERON_COUNT);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 } catch (RemoteExecuteException e) {
 	e.printStackTrace();
 }
```