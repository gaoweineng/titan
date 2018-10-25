# TelephonyModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

Telephony服务管理模块.对物理按键如电源键及虚拟按键的管理接口. 通过SystemFunctionService.getFunction(TelephonyModule.class)获取实例。

## 常量

> ### networkType : int
 
public boolean setPreferredNetworkType(int networkType) throws ServiceDeathException

#### 功能
网络首选项可选值。

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_WCDMA_PREF</td>
  <td width="60">0</td>
  <td>GSM/WCDMA (首选WCDMA)</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_GSM_ONLY</td>
  <td width="60">1</td>
  <td>仅GSM</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_WCDMA_ONLY</td>
  <td width="60">2</td>
  <td>仅WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_GSM_UMTS</td>
  <td width="60">3</td>
  <td>GSM/WCDMA (根据PRL, 自动模式)</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_CDMA</td>
  <td width="60">4</td>
  <td>CDMA and EvDo (根据PRL, 自动模式)</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_CDMA_NO_EVDO</td>
  <td width="60">5</td>
  <td>仅CDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_EVDO_NO_CDMA</td>
  <td width="60">6</td>
  <td>仅EvDo</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_GLOBAL</td>
  <td width="60">7</td>
  <td>GSM/WCDMA, CDMA, EvDo (根据PRL, 自动模式)</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_LTE_CDMA_EVDO</td>
  <td width="60">8</td>
  <td>LTE, CDMA, EvDo</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_LTE_GSM_WCDMA</td>
  <td width="60">9</td>
  <td>LTE, GSM/WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_LTE_CDMA_EVDO_GSM_WCDMA</td>
  <td width="60">10</td>
  <td>LTE, CDMA, EvDo, GSM/WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_LTE_ONLY</td>
  <td width="60">11</td>
  <td>LTE 唯一模式</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_LTE_WCDMA</td>
  <td width="60">12</td>
  <td>LTE/WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_ONLY</td>
  <td width="60">13</td>
  <td>仅TD-SCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_WCDMA</td>
  <td width="60">14</td>
  <td>TD-SCDMA, WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_LTE</td>
  <td width="60">15</td>
  <td>TD-SCDMA, LTE</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_GSM</td>
  <td width="60">16</td>
  <td>TD-SCDMA, GSM</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_GSM_LTE</td>
  <td width="60">17</td>
  <td>TD-SCDMA,GSM, LTE</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_GSM_WCDMA</td>
  <td width="60">18</td>
  <td>TD-SCDMA, GSM/WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_WCDMA_LTE</td>
  <td width="60">19</td>
  <td>TD-SCDMA, WCDMA, LTE</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_GSM_WCDMA_LTE</td>
  <td width="60">20</td>
  <td>TD-SCDMA, GSM/WCDMA, LTE</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_CDMA_EVDO_GSM_WCDMA</td>
  <td width="60">21</td>
  <td>TD-SCDMA,EvDo,CDMA, GSM/WCDMA</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_TD_SCDMA_LTE_CDMA_EVDO_GSM_WCDMA</td>
  <td width="60">22</td>
  <td>TD-SCDMA/ LTE/GSM/ WCDMA, CDMA, EvDo</td>
</tr>
<tr>
  <td width="100">NETWORK_MODE_LTE_CDMA_EVDO_GSM</td>
  <td width="60">23</td>
  <td>LTE/CDMA/EvDo/GSM</td>
</tr>
</table>

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(TelephonyModule.class)接口获取实例。

> ### getSimRecord5F01

public String getSimRecord5F01() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取SIM卡特定位置5F01位置上记录信息.(通联特定SIM卡)。

##### 返回值
5F01位置记录信息。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- SIM卡状态错误	
	- 系统不支持

> ### getSimRecord5F2

public String getSimRecord5F02() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取SIM卡特定位置5F02位置上记录信息.(通联特定SIM卡)。

##### 返回值
5F02位置记录信息。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- SIM卡状态错误	
	- 系统不支持

> ### getIMEI

public String getIMEI(int slot) throws ServiceDeathException, RemoteExecuteException

##### 功能
获取指定卡槽的IMEI。

##### 参数
* slot：卡槽id, 取值范围[0, 1]

##### 返回值  
设备IMEI值, 卡槽不被支持，返回null。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### getDeviceId

public String getDeviceId(int slot) throws ServiceDeathException, RemoteExecuteException

##### 功能
获取设备ID, 例如, GSM的IMEI和CDMA电话的MEID或ESN。

##### 参数
* slot：卡槽id, 取值范围[0, 1]

##### 返回值  
设备ID值, 卡槽不被支持，返回null。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### getPreferredNetworkType

public int getPreferredNetworkType() throws ServiceDeathException, RemoteExecuteException

##### 功能
获取网络首选项类型。

##### 返回值  
网络首选项类型。参考值[networkType](#networkType)。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setPreferredNetworkType

public boolean setPreferredNetworkType(int networkType) throws ServiceDeathException

##### 功能
设置网络首选项类型。

##### 参数
* networkType: 网络首选项类型。参考值[networkType](#networkType)。

##### 返回值  
设置成功返回true, 否则返回false, 返回false时可通过 TitanContext.getLastError()获取错误码。
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。


## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	TelephonyModule telephony = service.getFunction(TelephonyModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```