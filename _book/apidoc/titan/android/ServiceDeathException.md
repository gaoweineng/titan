# ServiceDeathException	

##### extends java.lang.Exception #####
			
#### since 1.0.0 ####

## 概览

应用调用统一接口时，接口服务未运行时抛出此异常.服务未运行一般有以下情况:

* 服务未安装 
* 服务已安装但未启动 
* 服务运行过程中出现崩溃，崩溃后未重启 
