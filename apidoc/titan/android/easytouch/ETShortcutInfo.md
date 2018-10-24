# ETShortcutInfo		

##### extends android.os.Parcel  #####
		
#### since 1.0.0 ####

## 概览

悬浮球快捷菜单配置信息。

## 公开属性

<table border="0" cellspacing="0"  cellpadding="0" width="100%">
<tr>
  <th width="100" align="left">属性名</td>
  <th width="60" align="left">类型</td>
  <th align="left">说明</td>
</tr>
<tr>
  <td width="100">menuTitle</td>
  <td width="60">String</td>
  <td>在悬浮球上显示的菜单名称</td>
</tr>
<tr>
  <td width="100">packageName</td>
  <td width="60">String</td>
  <td>应用的包名</td>
</tr>
<tr>
  <td width="100">className</td>
  <td width="60">String</td>
  <td>应用的入口组件类名, 类名为全路径</td>
</tr>
<tr>
  <td width="100">showIndex</td>
  <td width="60">int</td>
  <td>应用显示在悬浮球上的位置, 以顺时针方向开始, 0表示位于悬浮球正上方</td>
</tr>
<tr>
  <td width="100">isLock</td>
  <td width="60">boolean</td>
  <td>设置应用是否锁定, 锁定后的应用无法通过悬浮球的菜单设置进行移除</td>
</tr>
</table>