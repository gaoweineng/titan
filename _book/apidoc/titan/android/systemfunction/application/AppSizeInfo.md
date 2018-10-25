# AppSizeInfo

##### implements android.os.Parcelable  #####
				
#### since 1.0.0 ####

## 概览

应用大小信息。
				
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
  <td>此统计数据的应用包名</td>
</tr>
<tr>
  <td width="100">userHandle</td>
  <td width="60">int</td>
  <td>N/A</td>
</tr>
<tr>
  <td width="100">codeSize</td>
  <td width="60">long</td>
  <td>代码大小,如APK</td>
</tr>
<tr>
  <td width="100">dataSize</td>
  <td width="60">long</td>
  <td>应用程序的内部数据大小。(例如,/data/data/&lt;app&gt;/)</td>
</tr>
<tr>
  <td width="100">cacheSize</td>
  <td width="60">long</td>
  <td>应用程序缓存数据大小。(例如,/data/data/&lt;app&gt;/cache)</td>
</tr>
<tr>
  <td width="100">externalCodeSize</td>
  <td width="60">long</td>
  <td>保存应用程序代码的外部存储上的安全容器的大小。</td>
</tr>
<tr>
  <td width="100">externalDataSize</td>
  <td width="60">long</td>
  <td>应用程序使用的外部数据的大小。(例如,&lt;sdcard&gt;/Android/data/&lt;app&gt;</td>
</tr>
<tr>
  <td width="100">externalCacheSize</td>
  <td width="60">long</td>
  <td>应用程序使用的外部高速缓存的大小(即SD卡上)。 如果这是数据目录的子目录，则将从外部数据大小中减去此大小。</td>
</tr>
<tr>
  <td width="100">externalMediaSize</td>
  <td width="60">long</td>
  <td>应用程序使用的外部介质大小。</td>
</tr>
<tr>
  <td width="100">externalObbSize</td>
  <td width="60">long</td>
  <td>放置在外部介质的OBB的大小。</td>
</tr>
</table>