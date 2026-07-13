---
title: MA 2.0快速加载模型
subtitle: MA 2.0快速加载模型
description: MyST Markdown can be used in JupyterLab with support for all MyST syntax as well as inline execution.
---

172.70.24.253为可通外网机器的ip
v2ray-windows-64目录下cmd执行v2ray.exe run
添加DNS服务
vi /etc/resolv.conf
添加 nameserver 172.70.24.253 IP 代理服务器ip

vi /etc/profile
追加
export http_proxy="http://172.70.24.253:1089"
export https_proxy="https://172.70.24.253:1089"
export ALL_PROXY=http://172.70.24.253:1089

source /etc/profile

Docker配置代理
 vi /etc/systemd/system/docker.service.d/http-proxy.conf
[Service]
Environment="HTTP_PROXY=http://172.70.24.253:1089"
Environment="HTTPS_PROXY=http://172.70.24.253:1089"
Environment="NO_PROXY=localhost,127.0.0.1"

关闭防火墙
sudo systemctl stop firewalld

yum源修改
备份 sudo cp /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
sudo wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.tuna.tsinghua.edu.cn/help/centos/centos7.repo

（3）重启 Docker 使配置生效
bash
sudo systemctl daemon-reload
sudo systemctl restart docker

(4) 清理缓存并测试
bash
sudo yum clean all     # 清除缓存
sudo yum makecache     # 重建缓存
sudo yum update curl   # 测试更新

快速查看系统概览：uname -a + hostnamectl + free -h + df -h + ip a
硬件详情：lscpu + lspci + lsblk + dmidecode
故障排查：dmesg + journalctl + top

