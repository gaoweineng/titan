# ComponentStatus
				
#### since 1.0.0 ####

## 概览

采集模块状态量包装类。

## 枚举类

> Level 

状态码等级

* S ： 正常
* E ： 故障
* W ： 警告

## 接口说明

> ### getEncoder

public String getEncoder()

##### 接口功能
获取编码定义方。

##### 返回值
编码定义方。

> ### getLevel

public Level getLevel()

##### 接口功能
获取状态码级别。

##### 返回值
状态码级别。

> ### getDescription

public String getDescription()

##### 接口功能
获取状态码简单描述。

##### 返回值
状态码简单描述 。

> ### getTagNo

public int getTagNo()

##### 接口功能
获取采集因子tagNo。

##### 返回值
采集因子tagNo。

> ### getFactorNo

public int getFactorNo()

##### 接口功能
获取采集因子factorNo。

##### 返回值
采集因子factorNo。

> ### getStatusCode

public String getStatusCode()

##### 接口功能
获取状态码，16进制表示的状态编码，如0x41。

##### 返回值
状态码。