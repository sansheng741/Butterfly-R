---
title:  Nmap渗透信息搜集用法

author: Radium-Bit

authorLink: ''

cover: https://cdn.jsdelivr.net/gh/radium-bit/res@latest/nmap.webp

date : 2020-11-14

tags: Nmap

---
**nmap是一个网络连接端扫描软件，用来扫描网上电脑开放的网络连接端。确定哪些服务运行在哪些连接端，并且推断计算机运行哪个操作系统（这是亦称 fingerprinting）。它是网络管理员必用的软件之一，以及用以评估网络系统安全。** 
  
# 常用指令  
  
{% note info %}
nmap -v 详细信息输出  
nmap -p 指定端口  
nmap -iL 扫描文件中的ip  
nmap -exclude 不扫描某些ip  
nmap -Pn 使用ping扫描，显式地关闭端口扫描，用于主机发现  
nmap -sn 使用ping扫描，进行端口扫描，假设主机都是up的  
nmap -sS 使用SYN扫描，不需要完成三次握手  
nmap -sT TCP connect扫描，需要完成三次握手，只适用于找出TCP和UDP端口  
nmap -sU 扫描UDP端口  
nmap -sF FIN扫描，用于探测防火墙状态，识别端口是否关闭，容易漏扫  
nmap -sV 扫描目标主机的端口和软件版本
nmap -sA ACK扫描，用于确认靶机是否开启防火墙    
nmap -O 远程检测操作系统和软件  
nmap -O --osscan-guess 猜测目标操作系统版本 
nmap -D <欺骗ip1, 欺骗ip2, 欺骗ip3......> <目标ip> 来源IP地址欺骗，使用-D选项可以指定多个ip地址，或者使用RND随机生成多个地址  
nmap -traceroute 路由跟踪  
nmap -A 综合扫描，包含1-10000的端口进行*ping扫描，操作系统扫描，脚本扫描，路由跟踪，服务探测*  
nmap -oN result.txt 将标准输出写入到指定文件中
nmap -oX result.xml 将输入写成xml的形式  
nmap -oS result.txt 将输出写成特殊符号的形式，内容跟-oN是一样的，只是字体变了而已  
nmap -oG result.txt 将输出写成特殊格式 
nmap -sC 根据端口识别服务自动调用默认脚本  
nmap --script<文件名> | <类别> | <目录> / | <表达式> [，...] 用于手动选择攻击/嗅探脚本 
nmap -T[0-5] 时间参数  
{% endnote %}
## nmap -T[0-5] 的时间参数
 **-T0** 用于躲避IDS，时间很长  
  **-T1** 用于躲避IDS，时间很长  
  **-T2** 降低了扫描速度，使用更小的带宽和目标主机资源对目标靶机进行扫描  
  **-T3** 默认模式，未做优化  
  **-T4** 假设用户具有合适及可靠的网络而加速对目标靶机的扫描  
  **-T5** 假设用户具有更好的网络或者愿意牺牲准确性而加速扫描
  
## nmap --script的详细用法列表
 
### auth  

    这些脚本处理目标系统上的身份验证凭据（或绕过它们）。实例包括x11-access，ftp-anon，和oracle-enum-users。使用蛮力攻击来确定凭据的脚本被放置在brute类别中。  
### broadcast  

    此类脚本通常通过在本地网络上广播来发现未在命令行上列出的主机。使用 newtargets script参数，以允许这些脚本自动将发现的主机添加到Nmap扫描队列中。  
### brute  

    这些脚本使用蛮力攻击来猜测远程服务器的身份验证凭据。NMAP包含了暴力破解几十个协议，包括脚本http-brute，oracle-brute，snmp-brute，等。  
### discovery  

    这些脚本试图通过查询公共注册表，启用SNMP的设备，目录服务等来主动发现有关网络的更多信息。示例包括html-title（获取网站的根路径的标题），smb-enum-shares（枚举Windows共享）和snmp-sysdescr（通过SNMP提取系统详细信息）。
### dos  

    此类别的脚本可能会导致拒绝服务。有时这样做是为了测试拒绝服务方法的漏洞，但更常见的是，测试传统漏洞所必需的副作用是不希望的。这些测试有时会使易受攻击的服务崩溃。
### exploit  

    这些脚本旨在积极利用某些漏洞。示例包括jdwp-exec和http-shellshock。
### external  

    此类别中的脚本可能会将数据发送到第三方数据库或其他网络资源。这样的一个示例是whois-ip，它与whois相关联服务器以了解目标地址。第三方数据库的运营商始终会记录您发送给他们的任何内容，在许多情况下，这些内容将包括您的IP地址和目标地址。大多数脚本严格地涉及扫描计算机和客户端之间的通信。任何不属于此类别的东西。
### fuzzer  

    该类别包含旨在向每个数据包中的服务器软件发送意外或随机字段的脚本。尽管此技术对于发现软件中未发现的错误和漏洞很有用，但它过程缓慢且占用大量带宽。此类脚本的一个示例是dns-fuzz，该脚本用域请求稍有缺陷的方式轰炸DNS服务器，直到该服务器崩溃或经过用户指定的时间限制为止。
### intrusive  

    这些脚本无法归类， safe因为它们的风险太大，以至于它们会损坏目标系统，耗尽目标主机上的大量资源（例如带宽或CPU时间），或者被目标服务器认为是恶意的。系统管理员。实例是http-open-proxy与（要使用的目标服务器作为HTTP代理，其尝试）snmp-brute（其试图通过发送诸如公共值来猜测设备的SNMP团体字符串public，private和cisco）。除非脚本属于特殊version类别，否则应将其分类为safe或intrusive。
### malware  

    这些脚本测试目标平台是否感染了恶意软件或后门程序。示例包括smtp-strangeport，它监视运行在异常端口号上的SMTP服务器，以及auth-spoof，它检测到识别的欺骗守护程序，这些守护程序甚至在收到查询之前就提供了伪造的答案。这两种行为通常都与恶意软件感染相关。
### safe  

    并非旨在使服务崩溃，使用大量网络带宽或其他资源或利用安全漏洞的脚本被归类为safe。尽管与其他所有Nmap功能一样，我们不太可能冒犯远程管理员，但我们不能保证它们永远不会引起不良反应。其中大多数执行常规网络发现。示例为 ssh-hostkey（检索SSH主机密钥）和 html-title（从网页获取标题）。version类别中的脚本不是按照安全性分类的，但是其他不在其中的脚本都safe应该放在中intrusive。
### version  

    此特殊类别中的脚本是版本检测功能的扩展，无法明确选择。选择它们仅-sV在请求版本检测（）时运行。它们的输出无法与版本检测输出区分开，并且它们不产生服务或主机脚本结果。例子是skypev2-version，pptp-version和iax2-version。
### vuln  

    这些脚本检查特定的已知漏洞，并且通常仅在找到结果后才报告结果。示例包括realvnc-auth-bypass和afp-path-vuln。

[更多的资料可以参考官网](https://nmap.org/book/nse-usage.html)
[脚本详解和类型](https://nmap.org/nsedoc)

  
# 用法示例
  
1. 一个简单的万能扫描（*对124.0.0.1ping扫描，操作系统扫描，脚本扫描，路由跟踪，服务探测*）
```bash
nmap -T4 -A 127.0.0.1
```
2. 获取远程主机开放的端口、端口的服务、服务的版本、操作系统类型及其版本
```bash
nmap -sV -T4 -O --open <目标IP>
```
3. 进行SYN伪装IP的SBM Flood攻击
```bash
nmap -T5 -sS  --script=smb-flood -D <伪装的IP> <目标IP>
```
<font color=#0c74d6 size=5>***未完待续***</font>