# TimeZoneInfo

##### implements android.os.Parcelable  #####
				
#### since 1.0.0 ####

## 概览

该类用于指定时区的元信息。
				
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
  <td>时区代码, 如:America/Los_Angeles, GMT-08:00 or UTC</td>
</tr>
<tr>
  <td width="100">displayName</td>
  <td width="60">String</td>
  <td>时区名称</td>
</tr>
<tr>
  <td width="100">label</td>
  <td width="60">String</td>
  <td>语言名称：如:中文（简体）</td>
</tr>
<tr>
  <td width="100">DSTSavings</td>
  <td width="60">int</td>
  <td>此时区的最新夏令时（以毫秒为单位）, 相对于此时区的常规UTC偏移量.对于使用夏令时的时区，返回3600000（1小时），对于不使用夏令时的时区，例如Australia / Lord_Howe，使用其他值.）
</td>
</tr>
<tr>
  <td width="100">rawOffset</td>
  <td width="60">int</td>
  <td>此时区标准时间与UTC的偏移量（以毫秒为单位）</td>
</tr>
</table>