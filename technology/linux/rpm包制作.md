<!-- TITLE: Rpm包制作 -->
<!-- SUBTITLE: A quick summary of Rpm包制作 -->

打包
===
参考：https://fedoraproject.org/wiki/How_to_create_an_RPM_package/zh-cn

直接重新打包rpm
>rpmrebuild --package --notest-install -e xxx.rpm

解包
===
输出rpm的post字段

>rpm --scripts -qp xxx.rpm

输出rpm的spec文件(xxx已安装)
>rpmrebuild -s xxx.spec xxx