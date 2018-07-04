# 一行命令部署https网站(Deploy https website in one line command)

## 简介

你在本地(windows或者linux机器)写好了一个网站，甚至于本地架了 nginx,php, 而且已经能通过 [http://127.0.0.1](http://127.0.0.1) 访问了。怎么把本地网站上传到生产环境呢？并且部署全站 https 呢？

如果你感到不知所措，或者知道怎么做，却嫌麻烦懒得做，我猜下面的方法足够简单:

1. 本地安装 python(2或3都行), 装完 python 后使用 pip(pip3) 安装 ansible
1. `git clone https://github.com/mostevercxz/oneline_deploy_https_website.git && cd oneline_deploy_https_website`
1. 修改下需要自定义的变量，然后执行 `ansible-playbook -i ./hosts -v --ask-pass nginx_php7.yml`

## 需自己修改的选项

在 nginx_php7.yml 中

```text
certbot_email:在域名证书过期前，接收续期证书的提醒邮件
domain:购买的域名
local_website_root:本地网站文件存放目录，默认为当前目录下的 webroot 目录
```

在 hosts 中

```text
在 vps 节点下，将 1.1.1.1 改为新购买的云服务器 IP地址
如果云服务器只安装了 python3 (比如 ubuntu18.04 及以后的系统), 那 ansible_python_interpreter 要修改为 python3
```
