# LocationModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

位置模块管理类。 通过SystemFunctionService.getFunction(LocationModule.class)获取实例。

## 常量

> ### mode : int
 
boolean titan.android.systemfunction.location.LocationModule.setLocationMode(int mode) throws ServiceDeathException

#### 功能
位置模式的可选值。

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">LOCATION_MODE_OFF</td>
  <td width="60">0</td>
  <td>关闭位置服务</td>
</tr>
<tr>
  <td width="100">LOCATION_MODE_SENSORS_ONLY</td>
  <td width="60">1</td>
  <td>仅限设备, 使用GPS确定位置</td>
</tr>
<tr>
  <td width="100">LOCATION_MODE_BATTERY_SAVING</td>
  <td width="60">2</td>
  <td>耗电量低, 使用WLAN和移动网络确定位置</td>
</tr>
<tr>
  <td width="100">LOCATION_MODE_HIGH_ACCURACY</td>
  <td width="60">3</td>
  <td>准确度高, 使用GPS、WLAN和移动网络确定位置</td>
</tr>
</table>

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(LocationModule.class)接口获取实例。

> ### getLocationMode

public int getLocationMode() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取当前位置模式。

##### 返回值
当前位置模式。参考值[mode](#mode)
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setLocationMode

public boolean setLocationMode(int mode) throws ServiceDeathException

##### 功能
设置位置模式。错误码可通过{@link TitanContext#getLastError()}查询。

##### 参数
* mode：位置模式。参考值[mode](#mode)

##### 返回值  
设置成功, 返回 true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 系统不支持

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	LocationModule location = service.getFunction(LocationModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```