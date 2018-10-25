# NfcModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

NFC模块管理类。 通过SystemFunctionService.getFunction(NfcModule.class)获取实例。

## 常量

> ### state : int
 
public int getNfcState() throws ServiceDeathException, RemoteExecuteException

#### 功能
NFC模块状态可选值。

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">NFC_NOT_SUPPORTED</td>
  <td width="60">0</td>
  <td>设备不支持NFC</td>
</tr>
<tr>
  <td width="100">NFC_ENABLED</td>
  <td width="60">1</td>
  <td>启用NFC功能</td>
</tr>
<tr>
  <td width="100">NFC_DISENABLED</td>
  <td width="60">2</td>
  <td>关闭NFC功能</td>
</tr>
</table>

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(NfcModule.class)接口获取实例。

> ### getNfcState

public int getNfcState() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取NFC状态。

##### 返回值
当前位置模式。参考值[state](#state)
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setNfcState

public boolean setNfcState(int state) throws ServiceDeathException

##### 功能
设置NFC状态。错误码可通过{@link TitanContext#getLastError()}查询。

##### 参数
* state：位置模式。取值有：
	* NFC_ENABLED
	* NFC_DISENABLED

##### 返回值  
设置成功, 返回 true, 否则返回false。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 参数错误
	- 设备不支持
	- 系统不支持

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	NfcModule nfc = service.getFunction(NfcModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```