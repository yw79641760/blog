---
title: Kali Linux常用工具汇编
date created: 2025-07-27
date modified: 2025-07-27
description: A compilation of essential tools for Kali Linux security tasks.
tags:
  - Linux
  - Security
  - Tech
---

# 工具汇编

| 类别     | 名称                             | 功能                                 | 更多描述                                                                                       |
| -------- | -------------------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------- |
| 信息收集 | dnsenum                          | 服务枚举                             | 收集组织内用户名、计算机名称、IP地址等信息                                                     |
|          | snmpwalk                         | 网络信息收集                         | 使用snmp GETNEXT请求                                                                           |
|          | dmitry                           | 判断目标网络的IP地址范围             |                                                                                                |
|          | scapy                            | 执行并行路由跟踪                     |                                                                                                |
|          | nping                            | 识别活动主机                         |                                                                                                |
|          | nmap/Zenmap                      | 开放端口扫描                         | 包括操作系统指纹识别、服务指纹识别等                                                           |
|          | Wireshark                        | 抓包及分析                           |                                                                                                |
|          | p0f                              | 数据包分析                           |                                                                                                |
|          | Maltego                          | 信息收集与取证                       | 邮件地址、服务器信息、WHOIS查询等                                                              |
| 漏洞评估 | Nessus                           | 漏洞检测                             |                                                                                                |
|          | OpenVAS                          | 开放漏洞评估                         |                                                                                                |
| 漏洞利用 | Metasploit                       | 漏洞利用瑞士军刀                     | Armitage图形化，MSFCLI或MSFConsole获得主机访问权，Meterpreter传递载荷，Autopwn浏览器自动化攻击 |
| 权限提升 | Metasploit Meterpreter incognito | 模拟令牌                             |                                                                                                |
|          | Meterpreter shell                | 本地提权攻击                         |                                                                                                |
|          | SET/se-toolkit                   | 社会工程工具包                       |                                                                                                |
|          | keyscan_start/keyscan_dump       | 收集受害者数据（记录用户击键信息）   |                                                                                                |
|          | irb                              | 清理踪迹（日志移除）                 | 一个Ruby解释器shell                                                                            |
|          | persistence                      | 创建永久后门                         |                                                                                                |
|          | Ettercap                         | 中间人攻击（MITM）                   | 窃听目标与别人的通信，嗅探，ARP毒化                                                            |
| 密码攻击 | Hydra                            | 密码破解器                           | 支持多种协议，但会产生噪声，增加被侦测到的可能                                                 |
|          | Medusa                           | 获取路由器访问权限                   |                                                                                                |
|          | John the Ripper                  | 破解Windows安全访问管理器文件（SAM） |                                                                                                |
|          | Crunch                           | 生成密码字典                         |                                                                                                |
|          | RainbowCrack                     | 生成彩虹表                           | 彩虹表是特殊密码字典，使用哈希值代替标准字典密码                                               |
|          | OclHashcat-plus                  | 破解密码                             | 需使用Nvidia CUDA或ATI Stream支持的显卡实现                                                    |
|          | SUCrack                          | 物理访问攻击                         | 通过su执行本地用户账户暴力破解                                                                 |
| 无线攻击 | AirCrack                         | WEP，WPA/WPA2无线网络破解            |                                                                                                |
|          | Gerix                            | 无线网络自动化破解，伪造接入点AP     |                                                                                                |
|          | arpspoof                         | URL流量操控                          |                                                                                                |
|          | iptables                         | 端口重定向                           | 将安全端口重定向到非安全端口                                                                   |

# 参考

1. 《Kali Linux Cookbook》- https://book.douban.com/subject/25873820/
