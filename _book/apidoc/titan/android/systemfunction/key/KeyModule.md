# KeyModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

按键模块管理类.对物理按键如电源键及虚拟按键的管理接口. 通过SystemFunctionService.getFunction(KeyModule.class)获取实例。

## 常量

> ### powerKeyState : int
 
public boolean titan.android.systemfunction.key.KeyModule.setPowerKeyState(int powerKeyState) throws ServiceDeathException

#### 功能
按压类型的状态的可选值。

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">POWER_KEY_SHORT_LONG_PRESS_ENABLED</td>
  <td width="60">1</td>
  <td>设置电源键短按和长按都可用</td>
</tr>
<tr>
  <td width="100">POWER_KEY_SHORT_LONG_PRESS_DISABLED</td>
  <td width="60">2</td>
  <td>设置电源键短按和长按都不可用</td>
</tr>
<tr>
  <td width="100">POWER_KEY_ONLY_SHORT_PRESS_DISABLED</td>
  <td width="60">3</td>
  <td>设置电源键短按不可用,但长按可用</td>
</tr>
</table>

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(KeyModule.class)接口获取实例。

> ### isHomeKeyEnabled

public boolean isHomeKeyEnabled() throws ServiceDeathException, RemoteExecuteException

##### 功能
检查Home键是否可用。

##### 返回值
Home键可用返回true, 否则返回false
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setHomeKeyEnabled

public boolean setHomeKeyEnabled(boolean enabled) throws ServiceDeathException

##### 功能
启用/禁用Home键。错误码可通过{@link TitanContext#getLastError()}查询。

##### 参数
* enabled：true 启用, false 禁用。

##### 返回值  
设置成功, 返回 true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### isNavigationBarEnabled

public boolean isNavigationBarEnabled() throws ServiceDeathException

##### 功能
检查虚拟导航条是否可用。在有虚拟导航条的终端上可用，如P950/P990.无虚拟导航条的终端此接口始终返回true。错误码可通过 {@link TitanContext#getLastError()}查询。

##### 返回值
如果虚拟导航条可用, 返回 true, 否则返回 false
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setNavigationBarEnabled

public boolean setNavigationBarEnabled(boolean enabled) throws ServiceDeathException

##### 功能
启用/禁用虚拟导航条。在有虚拟导航条的终端上可用，如P950/P990.无虚拟导航条的终端此接口始终返回true, 但设置无效。错误码可通过 {@link TitanContext#getLastError()}查询

##### 参数
* enabled：true 启用, false 禁用。

##### 返回值  
设置成功, 返回 true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setPowerKeyState

public boolean setPowerKeyState(int powerKeyState) throws ServiceDeathException

##### 功能
设置电源键状态.电源键包含短按和长按两种按压类型。错误码可通过 {@link TitanContext#getLastError()}查询。

##### 参数
* powerKeyState：表示按压类型的状态，参考值[powerKeyState](#powerKeyState)。

##### 返回值  
设置成功, 返回 true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误
	- 系统不支持

> ### getPowerKeyState

public int getPowerKeyState() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取电源键状态。错误码可通过 {@link TitanContext#getLastError()}查询。

##### 返回值  
当前电源键状态，参考值[powerKeyState](#powerKeyState)。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。


## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	KeyModule key = service.getFunction(KeyModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```