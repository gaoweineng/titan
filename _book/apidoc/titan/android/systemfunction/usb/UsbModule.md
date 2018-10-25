# UsbModule

##### extends titan.android.core.TitanModule  #####
				
#### since 1.0.0 ####

## 概览

USB模块管理类。 通过SystemFunctionService.getFunction(UsbModule.class)获取实例。

## 枚举类

> UsbMode 

USB功能枚举

* NONE： 不设置功能
* MTP ： MTP(默认值)
* PTP ： PTP
* MASS_STORAGE ： MASS_STORAGE

## 方法说明

> ### 构造方法

不支持应用直接实例化，而是通过SystemFunctionService.getFunction(UsbModule.class)接口获取实例。

> ### isFunctionEnabled

public boolean isFunctionEnabled(@NonNull UsbMode usbMode) throws ServiceDeathException, RemoteExecuteException

##### 功能
检查USB功能是否启用。

##### 参数
* usbMode ：USB功能模式, 不可为null。参考[UsbMode](#枚举类)。

##### 返回值
功能已启用返回true, 否则返回false
	
##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 系统不支持

> ### setCurrentFunction

public void setCurrentFunction(UsbMode usbMode) throws ServiceDeathException, RemoteExecuteException

##### 功能
设置当前USB功能. 应用可注册广播监听设置结果。
```
public final BroadcastReceiver setUsbFunctionReceiver = new BroadcastReceiver() {
 	@Override
 	public void onReceive(Context context, Intent intent) {
 		String action = intent.getAction();
 		if (action.equals(UsbManager.ACTION_USB_STATE)) {
 			boolean connected = intent.getBooleanExtra("connected", false);
 			boolean configured = intent.getBooleanExtra("configured", false);
 			boolean function_adb = intent.getBooleanExtra("adb", false);
 			boolean function_mtp = intent.getBooleanExtra("mtp", false);
 			boolean function_ptp = intent.getBooleanExtra("ptp", false);
 		}
 	}
 };
```
注册动态广播：
```
@Override
 public void onResume() {
 	super.onResume();
 	IntentFilter intentFilter = new IntentFilter();
 	intentFilter.addAction(UsbManager.ACTION_USB_STATE);
 	getActivity().registerReceiver(setUsbFunctionReceiver, intentFilter);
 }
```

##### 参数
* usbMode：USB功能模式, 不可为null。参考[UsbMode](#枚举类)。

##### 异常
* ServiceDeathException：远程服务未运行时抛出。
* RemoteExecuteException：接口执行过程异常, 以下情况会抛出异常
	- 应用无权限
	- 参数错误
	- 系统不支持

## 编程示例：

```
TitanContext titanContext = TitanContext.getTitanContext(context);
 try {
 	SystemFunctionService service = titanContext.getService(SystemFunctionService.class);
 	UsbModule usb = service.getFunction(UsbModule.class);
 } catch (ServiceNotFoundException e) {
 	e.printStackTrace();
 } catch (ServiceDeathException e) {
 	e.printStackTrace();
 }
```