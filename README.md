# Debian-Ubuntu-BBR-POWERED
## 准备:
使用前,请确认能够开启BBR.
可参考: Debian/Ubuntu 开启 TCP BBR 拥塞算法
或者直接执行此命令进行开启.

```
wget --no-check-certificate -qO 'BBR.sh' 'https://raw.githubusercontent.com/yanshibin/Debian-Ubuntu-TCP-BBR-/master/BBR.sh' && chmod a+x BBR.sh && bash BBR.sh -f
```
注意:执行此命令会自动重启.
一键地址:
```
wget --no-check-certificate -qO 'BBR_POWERED.sh' 'https://moeclub.org/attachment/LinuxShell/BBR_POWERED.sh' && chmod a+x BBR_POWERED.sh && bash BBR_POWERED.sh
```
指定内核版本(以v4.11.9内核版本为例):
```
wget --no-check-certificate -qO 'BBR_POWERED.sh' 'https://moeclub.org/attachment/LinuxShell/BBR_POWERED.sh' && chmod a+x BBR_POWERED.sh && bash BBR_POWERED.sh -f v4.11.9
```
### 说明:
  执行过程中会重新编译模块.
  模块默认为开机自动加载.
  模块名称:tcp_bbr_powered
  可用 modprobe tcp_bbr_powered 命令进行加载模块.
  可执行 lsmod |grep 'bbr_powered' 
  结果不为空,则加载模块成功
  可执行 sysctl -w net.ipv4.tcp_congestion_control=bbr_powered 使用此模块.
  以上只是说明,直接使用一键脚本即可.
### 注意事项:
  如遇报错:Error! Header not be matched by Linux Kernel.
  请用使用本博客提供的脚本重新开启BBR,或使用-f参数.可参考本篇中的准备步骤.
  如遇报错:Error! Install make或Error! Install gcc.
  首先尝试apt-get update,再次执行此脚本.
  如果未解决想办法自行安装gcc(>=4.9),或切换系统后再试.
  本脚本在Debian8,Debian9,Ubuntu16.04上通过测试.
### 引用评论中提供的在Ubuntu安装gcc-4.9的方法:
```
  apt-get install -y software-properties-common
  add-apt-repository ppa:ubuntu-toolchain-r/test
  apt-get update
  apt-get -y install g++-4.9
```
