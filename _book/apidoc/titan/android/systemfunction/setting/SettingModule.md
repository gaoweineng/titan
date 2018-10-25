# SettingModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

系统设置相关的管理类.通过此接口, 可以设置系统语言, 时间/时区, 输入法等, 以及获取系统当前有关设置信息。 通过SystemFunctionService.getFunction(SettingModule.class)获取实例。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(SettingModule.class)接口获取实例。

> ### getCurrentIME

public IMEInfo getCurrentIME() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取系统当前启用的输入法信息。

##### 返回值
输入法元信息。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持
	- 未设置输入法

> ### setCurrentIME

public boolean setCurrentIME(@NonNull String packageName, @NonNull String className) throws ServiceDeathException

##### 功能
设置输入法。

##### 参数
* packageName：输入法包名, <b>不能为null</b>。
* className：输入法全路径包名, <b>不能为null</b>。

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### getInstalledIMEList

public List<IMEInfo> getInstalledIMEList() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取已安装的输入法列表。

##### 返回值
输入法列表, 当未安装输入法时, 列表长度为0, 但不为空。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setSystemLanguage

public boolean setSystemLanguage(@NonNull String languageCode, @NonNull String countryCode) throws ServiceDeathException

##### 功能
设置系统语言。

##### 参数
* languageCode：语言代码, <b>不能为null</b>。
* countryCode：国家或地区代码, <b>不能为null</b>。
	
##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。


> ### getLanguageList

public List<LanguageInfo> getLanguageList() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取系统支持的语言列表。

##### 返回值
语言列表。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### getCurrentScreenTimeout

public int getCurrentScreenTimeout() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取屏幕超时休眠时间。

##### 返回值
休眠时间, 单位毫秒。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setScreenTimeout

public boolean setScreenTimeout(int timeout) throws ServiceDeathException

##### 功能
设置屏幕超时休眠时间, 当屏幕一段时间无操作时, 系统进入休眠。

##### 参数
* timeout：超时时间, 表示一段时间后无操作, 系统进入休眠，单位毫秒。参考值：
	* -1:永不休眠 
	* 15000:15秒后休眠 
	* 30000:30秒后休眠 
	* 60000:1分钟后休眠 
	* 120000:2分钟后休眠 
	* 300000:5分钟后休眠 
	* 600000:10分钟后休眠 
	* 1800000:30分钟后休眠 

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### getScreenTimeoutList

public List<Integer> getScreenTimeoutList() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取系统支持的屏幕超时休眠时间列表。

##### 返回值
休眠时间列表。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### getCurrentTimeZone

public TimeZoneInfo getCurrentTimeZone() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取系统当前时区。

##### 返回值
时区元信息。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setTimeZone

public boolean setTimeZone(@NonNull String id) throws ServiceDeathException

##### 功能
设置系统时区。

##### 参数
* id: 时区id, 不可为null

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setAutomaticTimeZoneEnabled

public boolean setAutomaticTimeZoneEnabled(boolean enabled) throws ServiceDeathException, RemoteExecuteException

##### 功能
启用/禁用自动确定时区。

##### 参数
* enabled: true表示启用, false表示禁用

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### getTimeZoneList

public List<TimeZoneInfo> getTimeZoneList() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取系统支持的时区列表。

##### 返回值
时区列表。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### getSystemTime

public long getSystemTime() throws ServiceDeathException, RemoteExecuteException 

##### 功能
获取系统时间. 无论系统的时区如何，此方法始终返回UTC时间。 这通常被称为“Unix时间”或“纪元时间”. 使用java.text.DateFormat实例格式化此时间。

##### 返回值
返回自1970年1月1日00：00：00.0 UTC以来的当前时间（以毫秒为单位）。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setSystemTime

public boolean setSystemTime(long time) throws ServiceDeathException 

##### 功能
设置系统时间。

##### 参数
time : 系统时间, 以毫秒为单位。

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setAutomaticTimeEnabled

public boolean setAutomaticTimeEnabled(boolean enabled) throws ServiceDeathException, RemoteExecuteException 

##### 功能
启用/禁用自动确定时间。

##### 参数
enabled: true表示启用, false表示禁用。

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setCustomBootAnimation

public boolean setCustomBootAnimation(@NonNull String zipPath) throws ServiceDeathException 

##### 功能
自定义开机动画. 设置开机动画接口不检查zip包内的动画文件是否合法, 需要开发者自行检查是否符合动画规则。可通过resetBootAnimation() 恢复默认值。

##### 参数
zipPath: 动画文件绝对路径, 不可为null。

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### resetBootAnimation

public boolean resetBootAnimation() throws ServiceDeathException

##### 功能
恢复开机动画, 使用系统默认的开机动画。

##### 返回值
恢复成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### setCellularDataEnabled

public boolean setCellularDataEnabled(boolean enabled) throws ServiceDeathException

##### 功能
启用/禁用移动网络。

##### 参数
enabled ： true表示启用, false表示禁用

##### 返回值
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。

> ### isCellularDataEnabled

public boolean isCellularDataEnabled() throws ServiceDeathException, RemoteExecuteException

##### 功能
检查移动网络是否启用。

##### 返回值
启用返回true, 禁用返回false。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持


## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	SettingModule setting = service.getFunction(SettingModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```