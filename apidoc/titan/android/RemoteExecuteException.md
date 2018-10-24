# RemoteExecuteException	

##### extends java.lang.Exception #####
			
#### since 1.0.0 ####

## 概览

系统统一接口功能执行异常。 

应用使用统一API接口时，当出现以下几种情况时会抛出RemoteExecuteException异常或其子类异常:

* 参数错误时抛出 RemoteExecuteException。
* 应用无权限时抛出 NotPermissionException。
* 设备不支持,如设备不具备执行此接口的条件时抛出 DeviceNotSupportedException。 
* 功能不支持,如系统服务未升级到满足该接口的版本或与远程服务交互异常时抛出MethodNotSupportedException。

## 子类

* [DeviceNotSupportedException](apidoc/titan/android/DeviceNotSupportedException.md)
* [MethodNotSupportedException](apidoc/titan/android/MethodNotSupportedException.md)
* [NotPermissionException](apidoc/titan/android/NotPermissionException.md)

## 方法说明

> ### getErrorCode

public int getErrorCode()	

##### 功能

获取异常错误码.

##### 返回值
错误码。参阅 [错误码](common/Errors.md)。

> ### getLocalizedMessage

public String getLocalizedMessage()	

##### 功能

获取异常信息。

##### 返回值
异常信息，包含错误码。参阅 [错误码](common/Errors.md)。
