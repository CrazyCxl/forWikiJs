<!-- TITLE: Systemed -->
<!-- SUBTITLE: A quick summary of Systemed -->

# journalctl

设置系统coredump保存时间为两天：
>journalctl --vacuum-time=2d

# systemctl
<table>
<tr><td>任务</td><td>旧指令</td><td>新指令</td></tr>
<tr><td>使某服务自动启动</td><td>chkconfig –level 3 httpd on</td><td>systemctl enable httpd.service</td></tr>
<tr><td>使某服务不自动启动</td><td>chkconfig –level 3 httpd off</td><td>systemctl disable httpd.service</td>
</tr>
<tr><td>检查服务状态</td>
<td>service httpd status</td>
<td>systemctl status httpd.service</td>
</tr>
<tr>
<td>显示所有已启动的服务</td>
<td>chkconfig –list</td>
<td>systemctl list-units –type=service</td>
</tr>
<tr>
<td>启动某服务</td>
<td>service httpd start</td>
<td>systemctl start httpd.service</td>
</tr>
<tr>
<td>停止某服务</td>
<td>service httpd stop</td>
<td>systemctl stop httpd.service</td>
</tr>
<tr>
<td>重启某服务</td>
<td>service httpd restart</td>
<td>systemctl restart httpd.service</td>
</tr>
</table>

### ps:
service配置文件路径：*/usr/lib/systemd/system/*