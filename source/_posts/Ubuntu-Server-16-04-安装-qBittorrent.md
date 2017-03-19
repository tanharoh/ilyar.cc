---
title: Ubuntu Server 16.04 安装 qBittorrent
date: 2017-03-19 11:58:29
tags:
---
通过PPA安装
```bash
sudo add-apt-repository ppa:qbittorrent-team/qbittorrent-stable

sudo apt update && sudo apt install qbittorrent-nox
```
创建服务
```bash
sudo vim /etc/systemd/system/qbittorrent-nox.service
```
修改UserName为你的用户名，需要有sudo权限
```bash
[Unit]
Description=qBittorrent Daemon Service
After=network.target

[Service]
Type=forking
User=UserName    #修改为你的用户名
ExecStart=/usr/bin/qbittorrent-nox -d

[Install]
WantedBy=multi-user.target
```
启动服务
```bash
sudo systemctl start qbittorrent-nox
```
设置为开机启动
```bash
sudo systemctl enable qbittorrent-nox
```
检查服务状态
```bash
systemctl status qbittorrent-nox
```
访问网页
```
服务器IP:8080

用户名:admin　 密码:adminadmin
```
修改网页端密码, 在Tools->Options

![修改密码](/images/qbittorrent-change-pass.png)