# ApplicationModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

应用模块管理类. 通过SystemFunctionService.getFunction(ApplicationModule.class)获取实例。

## 常量

> ### intervalType : int
 
public List<UsageStatsInfo> queryUsageStats(int intervalType, long beginTime, long endTime) throws ServiceDeathException, RemoteExecuteException

#### 功能
统计数据的时间间隔。

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">USAGE_STATS_INTERVAL_DAILY</td>
  <td width="60">0</td>
  <td>以天为时间间隔</td>
</tr>
<tr>
  <td width="100">USAGE_STATS_INTERVAL_WEEKLY</td>
  <td width="60">1</td>
  <td>以周为时间间隔</td>
</tr>
<tr>
  <td width="100">USAGE_STATS_INTERVAL_MONTHLY</td>
  <td width="60">2</td>
  <td>以月为时间间隔</td>
</tr>
<tr>
  <td width="100">USAGE_STATS_INTERVAL_YEARLY</td>
  <td width="60">3</td>
  <td>以年为时间间隔</td>
</tr>
<tr>
  <td width="100">USAGE_STATS_INTERVAL_BEST</td>
  <td width="60">4</td>
  <td>在给定时间范围内使用最佳的时间间隔</td>
</tr>
</table>

> ### flags : int
 
public void silentlyUninstall(@NonNull String packageName, @NonNull SilentlyUninstallListener listener, int flags) throws ServiceDeathException, RemoteExecuteException

#### 功能
卸载应用的可选值。

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">DELETE_KEEP_DATA</td>
  <td width="60">1</td>
  <td>卸载应用的flags取值, 表示只卸载应用, 应用数据仍保存</td>
</tr>
<tr>
  <td width="100">DELETE_ALL_USERS</td>
  <td width="60">2</td>
  <td>卸载应用的flags取值, 表示为所有用户卸载应用</td>
</tr>
</table>

## 接口类 

### interface SilentlyInstallListener

静默安装回调接口。

> #### onInstallFinished

public void onInstallFinished(String packageName)

##### 功能
安装成功时回调。

##### 参数
* packageName：应用包名。

> #### onInstallError

public void onInstallError(int error, String packageName)

##### 功能
安装失败时回调。

##### 参数
* error：失败的错误码。
* packageName：应用包名，可能为null。

### interface SilentlyUninstallListener

静默卸载回调接口。

> #### onUnInstallFinished

public void onUnInstallFinished(String packageName)

##### 功能
卸载成功时回调。

##### 参数
* packageName：应用包名。

> #### onUnInstallError

public void onUnInstallError(int error, String packageName)

##### 功能
卸载失败时回调。

##### 参数
* error：失败的错误码。
* packageName：应用包名。

### interface AppSizeInfoObserver

获取应用大小信息回调接口。

> #### onCompleted

public void onCompleted(AppSizeInfo appSizeInfo, boolean succeeded)

##### 功能
计算应用大小结束时回调。

##### 参数
* appSizeInfo：应用大小信息。
* succeeded：获取结果, true表示获取成功, false表示获取失败。

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(ApplicationModule.class)接口获取实例。

> ### getAppSignInfo

public AppSignInfo getAppSignInfo(@NonNull String packageName) throws ServiceDeathException, RemoteExecuteException

##### 功能
获取应用签名信息。

##### 参数
* packageName：应用包名, <b>不能为null</b>。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误, 如包名为null
	- 包名指定的应用的未安装
	- 找不到应用的apk文件
	- 系统不支持
	- 应用未签名

> ### getAppSizeInfo

public void getAppSizeInfo(@NonNull String packageName, @NonNull AppSizeInfoObserver observer) throws ServiceDeathException, RemoteExecuteException

##### 功能
获取应用大小.获取应用大小数据需要持续一段时间，通过observer 回调返回应用大小。该接口非阻塞。

##### 参数
* packageName：应用包名, <b>不能为null</b>。
* observer：计算应用大小结束时回调, <b>不能为null</b>。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误, 如包名或回调对象为null
	- 包名指定的应用的未安装
	- 系统不支持

> ### queryUsageStats

public List<UsageStatsInfo> queryUsageStats(int intervalType, long beginTime, long endTime) throws ServiceDeathException, RemoteExecuteException

##### 功能
获取给定时间范围的应用程序使用统计信息。

##### 参数
* intervalType：统计数据的时间间隔, 参数值[intervalType](#intervalType)。
* beginTime：统计范围起始时间, beginTime在统计区间内。
* endTime：统计范围结束时间, endTime在统计区间外。

##### 返回值
统计信息列表, 当统计范围无使用数据时, 列表长度为0, 但不为空。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误
	- 系统不支持

> ### silentlyInstall

public void silentlyInstall(@NonNull String path, @NonNull SilentlyInstallListener listener) throws ServiceDeathException, RemoteExecuteException

##### 功能
安装apk。安装过程会持续一段时间, 结果通过listener 回调通知。 当应用已经被安装, 如果apk是合法的, 已安装应用将被替换。该接口非阻塞。

##### 参数
* path：apk绝对路径, <b>不能为null</b>。
* listener：安装完成通过该监听器回调, <b>不能为null</b>。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误
	- 系统不支持

> ### silentlyInstall

public void silentlyInstall(@NonNull String path, @NonNull SilentlyInstallListener listener, String installerPackageName) throws ServiceDeathException, RemoteExecuteException

##### 功能
安装apk。安装过程会持续一段时间, 结果通过listener 回调通知。 当应用已经被安装, 如果apk是合法的, 已安装应用将被替换。该接口非阻塞。

##### 参数
* path：apk绝对路径, <b>不能为null</b>。
* listener：安装完成通过该监听器回调, <b>不能为null</b>。
* installerPackageName：正在执行安装的应用程序的可选包名称. 这标识了包来自哪个市场, 未指定时为null。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误
	- 系统不支持

> ### silentlyUninstall

public void silentlyUninstall(@NonNull String packageName, @NonNull SilentlyUninstallListener listener) throws ServiceDeathException, RemoteExecuteException

##### 功能
卸载应用, 包括清空应用数据. 卸载应用会持续一段时间, 结果通过listener 回调通知。该接口非阻塞。

##### 参数
* packageName：被卸载应用的包名, <b>不能为null</b>。
* listener：卸载完成通过该监听器回调, <b>不能为null</b>。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误
	- 包名指定的应用未安装
	- 系统不支持

> ### silentlyUninstall

public void silentlyUninstall(@NonNull String packageName, @NonNull SilentlyUninstallListener listener, int flags) throws ServiceDeathException, RemoteExecuteException

##### 功能
卸载应用. 卸载应用会持续一段时间, 结果通过listener 回调通知。该接口非阻塞。

##### 参数
* packageName：被卸载应用的包名, <b>不能为null</b>。
* listener：卸载完成通过该监听器回调, <b>不能为null</b>。
* flags：卸载应用的可选值，参考值[flags](#flags)。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限	
	- 参数错误
	- 包名指定的应用未安装
	- 系统不支持

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	ApplicationModule application = service.getFunction(ApplicationModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```