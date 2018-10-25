# AppSignInfo

##### implements android.os.Parcelable  #####
				
#### since 1.0.0 ####

## 概览

应用签名信息。
				
## 公开属性

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">属性名</td>
  <th width="60" align="left">类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">rootCAId</td>
  <td width="60">String</td>
  <td>根证书ID</td>
</tr>
<tr>
  <td width="100">rootCAOwer</td>
  <td width="60">String</td>
  <td>根证书所有者</td>
</tr>
<tr>
  <td width="100">CAId</td>
  <td width="60">String</td>
  <td>工作证书ID</td>
</tr>
<tr>
  <td width="100">signer</td>
  <td width="60">int</td>
  <td>签名者</td>
</tr>
<tr>
  <td width="100">extendPermissions</td>
  <td width="60">List&lt;String&gt;</td>
  <td>扩展权限列表</td>
</tr>
</table>