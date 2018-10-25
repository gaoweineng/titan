# IMEInfo

##### implements android.os.Parcelable  #####
				
#### since 1.0.0 ####

## 概览

该类用于指定输入法的元信息。
				
## 公开属性

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">属性名</td>
  <th width="60" align="left">类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">id</td>
  <td width="60">String</td>
  <td>识别输入方法的唯一字符串Id, 由输入法组件生成的, 如:com.android.inputmethod.latin/.LatinIME</td>
</tr>
<tr>
  <td width="100">packageName</td>
  <td width="60">String</td>
  <td>输入法包名, 如:com.android.inputmethod.latin</td>
</tr>
<tr>
  <td width="100">serviceName</td>
  <td width="60">String</td>
  <td>输入法服务组件名称, 如:com.android.inputmethod.latin.LatinIME</td>
</tr>
<tr>
  <td width="100">className</td>
  <td width="60">String</td>
  <td>输入法服务组件全路径类名, 如:com.android.inputmethod.latin.LatinIME</td>
</tr>
<tr>
  <td width="100">settingsActivity</td>
  <td width="60">String</td>
  <td>返回为输入方法提供设置UI界面的类名称, 如:com.android.inputmethod.latin.settings.SettingsActivity, 如果没有与输入方法关联的设置活动，则为null</td>
</tr>
<tr>
  <td width="100">shortClassName</td>
  <td width="60">String</td>
  <td>输入法服务组件类名, 如:LatinIME</td>
</tr>
<tr>
  <td width="100">permission</td>
  <td width="60">String</td>
  <td>能够访问输入法服务所需权限的可选名称. 来自"permission" 属性. 如:android.permission.BIND_INPUT_METHOD</td>
</tr>
<tr>
  <td width="100">subtypeCount</td>
  <td width="60">int</td>
  <td>输入法支持的语言数目</td>
</tr>
<tr>
  <td width="100">isEnabled</td>
  <td width="60">boolean</td>
  <td>输入法是否启用</td>
</tr>
<tr>
  <td width="100">label</td>
  <td width="60">String</td>
  <td>输入法label</td>
</tr>
<tr>
  <td width="100">subtypeDisplayName</td>
  <td width="60">String</td>
  <td>输入法当前使用的语言名称</td>
</tr>
</table>