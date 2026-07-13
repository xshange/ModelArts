---
title: python在线机器下载安装包及依赖包，离线机器安装扩展包
short_title: python在线机器下载安装包及依赖包，离线机器安装扩展包
subject: Who
subtitle: python在线机器下载安装包及依赖包，离线机器安装扩展包
description: python在线机器下载安装包及依赖包，离线机器安装扩展包
---


##  下载安装包及依赖包🚀

```shell
#!/bin/bash
# prepare_ansible_offline.sh

echo "=== 准备 Ansible 离线安装包 ==="

# 配置 pip 阿里源
mkdir -p ~/.pip
cat > ~/.pip/pip.conf << 'EOF'
[global]
index-url = http://mirrors.aliyun.com/pypi/simple/

[install]
trusted-host = mirrors.aliyun.com
EOF

# 下载 Ansible 及依赖
mkdir -p ~/ansible-offline
cd ~/ansible-offline

pip3 download ansible \
    --platform manylinux2014_aarch64 \
    --python-version 3.9 \
    --only-binary :all: \
    -i http://mirrors.aliyun.com/pypi/simple/ \
    --trusted-host mirrors.aliyun.com \
    -d .

# 打包
cd ~
tar -czvf ansible-offline-aarch64-$(date +%Y%m%d).tar.gz ansible-offline/

echo "=== 离线包已生成 ==="
ls -lh ansible-offline-aarch64-*.tar.gz
```

## 离线机器安装扩展
```shell
#!/bin/bash
# install_ansible_offline.sh

echo "=== 离线安装 Ansible ==="

# 解压
tar -xzvf ansible-offline-aarch64-*.tar.gz
cd ansible-offline

# 一键安装所有包
pip3 install --no-index --find-links . *.whl

# 添加 PATH
export PATH=/usr/local/bin:$PATH
echo 'export PATH=/usr/local/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# 验证
echo "=== 验证安装 ==="
ansible --version
ansible-playbook --version
ansible localhost -m ping

echo "=== 安装完成 ==="
```
