# EasyTouchService

##### extends titan.android.core.TitanService  #####
				
#### since 1.0.0 ####

## 概览

EasyTouchService悬浮球服务代理接口. 不能直接实例化EasyTouchService，而是通过 TitanContext.getService(Class)接口, 传入参数 EasyTouchService.class 获取悬浮球服务代理对象. 

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过TitanContext.getService(EasyTouchService.class)接口获取实例。

> ### addETShortcut

public boolean addETShortcut(@NonNull ETShortcutInfo info, boolean replace) throws ServiceDeathException

##### 功能
添加悬浮快捷菜单。

##### 参数
* info：快捷菜单配置信息, 不可为null。
* replace: 当相同位置有其他应用快捷菜单时, 是否替换. true表示替换, false表示不替换。
	
##### 返回值
true表示添加成功, false表示添加失败. 可通过TitanContext.getLastError() 查询错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出

> ### getETShortcuts

public List<ETShortcutInfo> getETShortcuts() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取悬浮球已设置的快捷菜单信息。

##### 返回值
快捷菜单信息列表。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException:接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### removeETShortcut

public boolean removeETShortcut(@NonNull ETShortcutInfo info) throws ServiceDeathException

##### 功能
移除悬浮快捷菜单。

##### 参数
* info：快捷菜单配置信息, 不可为null。

##### 返回值
true表示移除成功, false表示移除失败. 可通过TitanContext.getLastError() 查询错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setEasyTouchEnabled

public boolean setEasyTouchEnabled(boolean enabled) throws ServiceDeathException

##### 功能
开启/关闭悬浮球。

##### 参数
* enabled：true表示开启, false表示关闭。

##### 返回值
true表示移除成功, false表示移除失败. 可通过TitanContext.getLastError() 查询错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setETShortcuts

public boolean setETShortcuts(@NonNull List<ETShortcutInfo> infos) throws ServiceDeathException

##### 功能
设置悬浮快捷菜单, 该接口将替换悬浮球上所有已设置的快捷菜单。

##### 参数
* infos：快捷菜单配置信息列表, 不可为null, 且列表至少有一项快捷菜单信息。

##### 返回值
true表示设置成功, false表示设置失败. 可通过TitanContext.getLastError() 查询错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### turnplateSliding

public boolean turnplateSliding(boolean sliding) throws ServiceDeathException

##### 功能
设置悬浮球转盘是否可转动。

##### 参数
* sliding：true表示允许转盘转动, false表示禁止转移转动。

##### 返回值
true表示设置成功, false表示设置失败. 可通过TitanContext.getLastError() 查询错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	EasyTouchService service = titanContext.getService(EasyTouchService.class);
	List<ETShortcutsInfo> infos = service.getETShortcuts();
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 } catch (RemoteExecuteException e) {
	e.printStackTrace();	
 }
```