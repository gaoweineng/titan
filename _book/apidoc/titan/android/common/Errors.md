# Errors				
#### since 1.0.0 ####

## 概览
系统统一接口返回值常量定义类。调用任何一个API，都可以通过TitanContext.getLastError()接口获取对应的错误码。

## 常量

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">名称</td>
  <th width="60" align="left">取值</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">NONE</td>
  <td width="60">0x00</td>
  <td>成功</td>
</tr>
<tr>
  <td width="100">NOTPERMISSION</td>
  <td width="60">0x10001</td>
  <td>应用无权限</td>
</tr>
<tr>
  <td width="100">METHOD_NOT_SUPPORTED</td>
  <td width="60">0x10002</td>
  <td>系统不支持, 一般是由于系统软件功能不存在或版本过低</td>
</tr>
<tr>
  <td width="100">DEVICE_NOT_SUPPORTED</td>
  <td width="60">0x10003</td>
  <td>设备不支持, 一般是由于终端不存在某一硬件模块, 如电池, NFC芯片等硬件模块</td>
</tr>
<tr>
  <td width="100">ERRPARAM</td>
  <td width="60">0x11001</td>
  <td>参数错误</td>
</tr>
<tr>
  <td width="100">APP_NOT_RUNNING</td>
  <td width="60">0x21001</td>
  <td>App未运行</td>
</tr>
<tr>
  <td width="100">APP_NOT_INSTALLED</td>
  <td width="60">0x21002</td>
  <td>App未安装</td>
</tr>
<tr>
  <td width="100">APK_NOT_FOUND</td>
  <td width="60">0x21003</td>
  <td>Apk文件未找到</td>
</tr>
<tr>
  <td width="100">APP_UNSIGNED</td>
  <td width="60">0x21004</td>
  <td>App未签名</td>
</tr>
<tr>
  <td width="100">BOOT_ANIMATION_ZIP_NOT_EXIST</td>
  <td width="60">0x22001</td>
  <td>开机动画zip包不存在</td>
</tr>
<tr>
  <td width="100">COPY_BOOT_ANIMATION_ZIP_FAIL</td>
  <td width="60">0x22002</td>
  <td>拷贝开机动画zip包到指定路径失败</td>
</tr>
<tr>
  <td width="100">CHMOD_BOOT_ANIMATION_ZIP_FIAL</td>
  <td width="60">0x22003</td>
  <td>修改开机动画文件权限失败</td>
</tr>
<tr>
  <td width="100">CURRENT_IME_IS_NULL</td>
  <td width="60">0x22004</td>
  <td>未设置当前输入法</td>
</tr>
<tr>
  <td width="100">IME_NOT_INSTALLED</td>
  <td width="60">0x22005</td>
  <td>输入法未安装</td>
</tr>
<tr>
  <td width="100">ERR_SIM_STATE</td>
  <td width="60">0x23001</td>
  <td>SIM卡状态错误</td>
</tr>
<tr>
  <td width="100">SET_PREFERRED_NETWORK_TYPE_FAIL</td>
  <td width="60">0x23002</td>
  <td>设置网络首选项失败</td>
</tr>
<tr>
  <td width="100">UNKNOWN_PREFERRED_NETWORK_TYPE</td>
  <td width="60">0x23003</td>
  <td>未知类型的网络首选项</td>
</tr>
</table>