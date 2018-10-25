# UsageStatsInfo

##### implements android.os.Parcelable  #####
				
#### since 1.0.0 ####

## 概览

指定时间范围内, 应用使用信息统计。
				
## 公开属性

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">属性名</td>
  <th width="60" align="left">类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">packageName</td>
  <td width="60">String</td>
  <td>包含使用情况统计信息的应用包名称</td>
</tr>
<tr>
  <td width="100">beginTimeStamp</td>
  <td width="60">long</td>
  <td>统计信息的开始时间, 以毫秒为单位</td>
</tr>
<tr>
  <td width="100">endTimeStamp</td>
  <td width="60">long</td>
  <td>统计信息的结束时间, 以毫秒为单位</td>
</tr>
<tr>
  <td width="100">lastTimeUsed</td>
  <td width="60">long</td>
  <td>最后一次使用此应用的时间点，以毫秒为单位</td>
</tr>
<tr>
  <td width="100">totalTimeInForeground</td>
  <td width="60">long</td>
  <td>应用在系统前台的总时间，以毫秒为单位</td>
</tr>
</table>