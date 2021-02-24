---
layout:     post
title:      初识metasploit渗透测试框架
subtitle:   metasploit基础
date:       2021-02-23
author:     BlackFrog-hub
header-img: img/msf_bg.png
catalog: true
tags:
    - metasploit

---

### 什么是metasploit？
- 

### 查看帮助命令-h,help,?
```bash
msf5 > workspace -h
Usage:
    workspace                  List workspaces
    workspace -v               List workspaces verbosely
    workspace [name]           Switch workspace
    workspace -a [name] ...    Add workspace(s)
    workspace -d [name] ...    Delete workspace(s)
    workspace -D               Delete all workspaces
    workspace -r <old> <new>   Rename workspace
    workspace -h               Show this help information

msf5 > help workspace
Usage:
    workspace                  List workspaces
    workspace -v               List workspaces verbosely
    workspace [name]           Switch workspace
    workspace -a [name] ...    Add workspace(s)
    workspace -d [name] ...    Delete workspace(s)
    workspace -D               Delete all workspaces
    workspace -r <old> <new>   Rename workspace
    workspace -h               Show this help information

msf5 > ? workspace    // 与前面两个命令一样，只是不能使用Tab补全
Usage:
    workspace                  List workspaces
    workspace -v               List workspaces verbosely
    workspace [name]           Switch workspace
    workspace -a [name] ...    Add workspace(s)
    workspace -d [name] ...    Delete workspace(s)
    workspace -D               Delete all workspaces
    workspace -r <old> <new>   Rename workspace
    workspace -h               Show this help information

```
### 返回msf控制台
```bash
msf5 exploit(windows/smb/ms10_046_shortcut_icon_dllloader) > back
msf5 > 
```
### 退出msfconsole 
```bash
msf5 > exit
root@kali:~# 
```

### connect命令 
```bash
msf5 > connect 192.168.1.6 8081
[*] Connected to 192.168.1.6:8081 (via: 0.0.0.0:0)
get /
HTTP/1.1 400 Bad Request
Date: Wed, 24 Feb 2021 12:59:12 GMT
Server: Apache/2.4.25 (Win32) OpenSSL/1.0.2j PHP/5.6.30
Vary: accept-language,accept-charset
Accept-Ranges: bytes
Connection: close
Content-Type: text/html; charset=utf-8
Content-Language: en
Expires: Wed, 24 Feb 2021 12:59:12 GMT

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
<title>Bad request!</title>
<link rev="made" href="mailto:postmaster@localhost" />
<style type="text/css"><!--/*--><![CDATA[/*><!--*/ 
    body { color: #000000; background-color: #FFFFFF; }
    a:link { color: #0000CC; }
    p, address {margin-left: 3em;}
    span {font-size: smaller;}
/*]]>*/--></style>
</head>

<body>
<h1>Bad request!</h1>
<p>


    Your browser (or proxy) sent a request that
    this server could not understand.

</p>
<p>
If you think this is a server error, please contact
the <a href="mailto:postmaster@localhost">webmaster</a>.

</p>

<h2>Error 400</h2>
<address>
  <a href="/">localhost</a><br />
  <span>Apache/2.4.25 (Win32) OpenSSL/1.0.2j PHP/5.6.30</span>
</address>
</body>
</html>
```
### show命令
- show指定功能模块
```bash
msf5 > show nops 

NOP Generators
==============

   #  Name             Disclosure Date  Rank    Check  Description
   -  ----             ---------------  ----    -----  -----------
   0  aarch64/simple                    manual  No     Simple
   1  armle/simple                      manual  No     Simple
   2  mipsbe/better                     manual  No     Better
   3  php/generic                       manual  No     PHP Nop Generator
   4  ppc/simple                        manual  No     Simple
   5  sparc/random                      manual  No     SPARC NOP Generator
   6  tty/generic                       manual  No     TTY Nop Generator
   7  x64/simple                        manual  No     Simple
   8  x86/opty2                         manual  No     Opty2
   9  x86/single_byte                   manual  No     Single Byte
```
- show options查看功能的各种参数
```bash
msf5 > show options 

Global Options:
===============

   Option             Current Setting      Description
   ------             ---------------      -----------
   ConsoleLogging     false                Log all console input and output
   LogLevel           0                    Verbosity of logs (default 0, max 3)
   MeterpreterPrompt  meterpreter  The meterpreter prompt string
   MinimumRank        0                    The minimum rank of exploits that will run without explicit confirmation
   Prompt             msf5                 The prompt string
   PromptChar         >                    The prompt character
   PromptTimeFormat   %Y-%m-%d %H:%M:%S    Format for timestamp escapes in prompts
   SessionLogging     false                Log all input and output for sessions
   TimestampOutput    false                Prefix all console output with a timestamp
```
### search命令
- 搜索指定类型
```bash
5 > search  type:post

Matching Modules
================

   #    Name                                                    Disclosure Date  Rank       Check  Description
   -    ----                                                    ---------------  ----       -----  -----------
   0    post/aix/hashdump                                                        normal     No     AIX Gather Dump Password Hashes
   1    post/android/capture/screen                                              normal     No     Android Screen Capture
   2    post/android/gather/hashdump                                             normal     No     Android Gather Dump Password Hashes for Android Systems
   3    post/android/gather/sub_info                                             normal     No     extracts subscriber info from target device
   4    post/android/gather/wireless_ap                                          normal     No     Displays wireless SSIDs and PSKs
   5    post/android/manage/remove_lock                         2013-10-11       normal     No     Android Settings Remove Device Locks (4.0-4.3)
   6    post/android/manage/remove_lock_root                                     normal     No     Android Root Remove Device Locks (root)
   7    post/apple_ios/gather/ios_image_gather                                   normal     No     iOS Image Gatherer
   8    post/apple_ios/gather/ios_text_gather                                    normal     No     iOS Text Gatherer
   9    post/brocade/gather/enum_brocade                                         normal     No     Brocade Gather Device General Information
   10   post/bsd/gather/hashdump                                                 normal     No     BSD Dump Password Hashes
   11   post/cisco/gather/enum_cisco                                             normal     No     Cisco Gather Device General Information
   12   post/firefox/gather/cookies                             2014-03-26       normal     No     Firefox Gather Cookies from Privileged Javascript Shell
   13   post/firefox/gather/history                             2014-04-11       normal     No     Firefox Gather History from Privileged Javascript Shell
   14   post/firefox/gather/passwords                           2014-04-11       normal     No     Firefox Gather Passwords from Privileged Javascript Shell
   15   post/firefox/gather/xss                                                  normal     No     Firefox XSS
   16   post/firefox/manage/webcam_chat                         2014-05-13       normal     No     Firefox Webcam Chat on Privileged Javascript Shell
   17   post/hardware/automotive/can_flood                                       normal     No     CAN Flood
   18   post/hardware/automotive/canprobe                                        normal     No     Module to Probe Different Data Points in a CAN Packet
   19   post/hardware/automotive/getvinfo                                        normal     No     Get the Vehicle Information Such as the VIN from the Target Module
```
- 搜素指定内容
```bash
msf5 > search ms08_067

Matching Modules
================

   #  Name                                 Disclosure Date  Rank   Check  Description
   -  ----                                 ---------------  ----   -----  -----------
   0  exploit/windows/smb/ms08_067_netapi  2008-10-28       great  Yes    MS08-067 Microsoft Server Service Relative Path Stack Corruption
```
- 搜索指定cve:ID
```bash
msf5 > search cve:2020

Matching Modules
================

   #   Name                                                        Disclosure Date  Rank       Check  Description
   -   ----                                                        ---------------  ----       -----  -----------
   0   auxiliary/admin/ldap/vmware_vcenter_vmdir_auth_bypass       2020-04-09       normal     Yes    VMware vCenter Server vmdir Authentication Bypass
   1   auxiliary/gather/vmware_vcenter_vmdir_ldap                  2020-04-09       normal     No     VMware vCenter Server vmdir Information Disclosure
   2   auxiliary/scanner/http/limesurvey_zip_traversals            2020-04-02       normal     No     LimeSurvey Zip Path Traversals
   3   exploit/linux/http/eyesofnetwork_autodiscovery_rce          2020-02-06       excellent  Yes    EyesOfNetwork AutoDiscovery Target Command Execution
   4   exploit/linux/http/nexus_repo_manager_el_injection          2020-03-31       excellent  Yes    Nexus Repository Manager Java EL Injection RCE
   5   exploit/linux/http/rconfig_ajaxarchivefiles_rce             2020-03-11       good       Yes    Rconfig 3.x Chained Remote Code Execution
   6   exploit/linux/http/unraid_auth_bypass_exec                  2020-02-10       excellent  Yes    Unraid 6.8.0 Auth Bypass PHP Code Execution
   7   exploit/linux/http/vestacp_exec                             2020-03-17       excellent  No     Vesta Control Panel Authenticated Remote Code Execution
   8   exploit/linux/misc/tplink_archer_a7_c7_lan_rce              2020-03-25       excellent  Yes    TP-Link Archer A7/C7 Unauthenticated LAN Remote Code Execution
   9   exploit/multi/browser/chrome_jscreate_sideeffect            2020-02-19       manual     No     Google Chrome 80 JSCreate side-effect type confusion exploit
   10  exploit/multi/http/horde_csv_rce                            2020-02-07       excellent  No     Horde CSV import arbitrary PHP code execution
   11  exploit/multi/http/liferay_java_unmarshalling               2019-11-25       excellent  Yes    Liferay Portal Java Unmarshalling via JSONWS RCE
   12  exploit/multi/http/playsms_template_injection               2020-02-05       excellent  Yes    PlaySMS index.php Unauthenticated Template Injection Code Execution
   13  exploit/osx/local/vmware_fusion_lpe                         2020-03-17       excellent  Yes    VMware Fusion USB Arbitrator Setuid Privilege Escalation
   14  exploit/unix/fileformat/metasploit_libnotify_cmd_injection  2020-03-04       excellent  No     Metasploit Libnotify Plugin Arbitrary Command Execution
   15  exploit/unix/local/opensmtpd_oob_read_lpe                   2020-02-24       average    Yes    OpenSMTPD OOB Read Local Privilege Escalation
   16  exploit/unix/smtp/opensmtpd_mail_from_rce                   2020-01-28       excellent  Yes    OpenSMTPD MAIL FROM Remote Code Execution
   17  exploit/windows/http/desktopcentral_deserialization         2020-03-05       excellent  Yes    ManageEngine Desktop Central Java Deserialization
   18  exploit/windows/http/exchange_ecp_viewstate                 2020-02-11       excellent  Yes    Exchange Control Panel ViewState Deserialization
   19  exploit/windows/http/sharepoint_workflows_xoml              2020-03-02       excellent  Yes    SharePoint Workflows XOML Injection
   20  exploit/windows/http/ssrs_navcorrector_viewstate            2020-02-11       excellent  Yes    SQL Server Reporting Services (SSRS) ViewState Deserialization
   21  exploit/windows/local/cve_2020_0796_smbghost                2020-03-13       good       Yes    SMBv3 Compression Buffer Overflow
   22  exploit/windows/misc/hp_operations_agent_coda_8c            2012-07-09       normal     Yes    HP Operations Agent Opcode coda.exe 0x8c Buffer Overflow
```
- 搜索带有指定的内容
```bash
msf5 > search name:mysql

Matching Modules
================

   #   Name                                               Disclosure Date  Rank       Check  Description
   -   ----                                               ---------------  ----       -----  -----------
   0   auxiliary/admin/mysql/mysql_enum                                    normal     No     MySQL Enumeration Module
   1   auxiliary/admin/mysql/mysql_sql                                     normal     No     MySQL SQL Generic Query
   2   auxiliary/scanner/mysql/mysql_authbypass_hashdump  2012-06-09       normal     No     MySQL Authentication Bypass Password Dump
   3   auxiliary/scanner/mysql/mysql_file_enum                             normal     No     MYSQL File/Directory Enumerator
   4   auxiliary/scanner/mysql/mysql_hashdump                              normal     No     MYSQL Password Hashdump
   5   auxiliary/scanner/mysql/mysql_login                                 normal     No     MySQL Login Utility
   6   auxiliary/scanner/mysql/mysql_schemadump                            normal     No     MYSQL Schema Dump
   7   auxiliary/scanner/mysql/mysql_version                               normal     No     MySQL Server Version Enumeration
   8   auxiliary/scanner/mysql/mysql_writable_dirs                         normal     No     MYSQL Directory Write Test
   9   auxiliary/server/capture/mysql                                      normal     No     Authentication Capture: MySQL
   10  exploit/linux/mysql/mysql_yassl_getname            2010-01-25       good       No     MySQL yaSSL CertDecoder::GetName Buffer Overflow
   11  exploit/linux/mysql/mysql_yassl_hello              2008-01-04       good       No     MySQL yaSSL SSL Hello Message Buffer Overflow
   12  exploit/multi/mysql/mysql_udf_payload              2009-01-16       excellent  No     Oracle MySQL UDF Payload Execution
   13  exploit/windows/mysql/mysql_mof                    2012-12-01       excellent  Yes    Oracle MySQL for Microsoft Windows MOF Execution
   14  exploit/windows/mysql/mysql_start_up               2012-12-01       excellent  Yes    Oracle MySQL for Microsoft Windows FILE Privilege Abuse
   15  exploit/windows/mysql/mysql_yassl_hello            2008-01-04       average    No     MySQL yaSSL SSL Hello Message Buffer Overflow
   16  exploit/windows/mysql/scrutinizer_upload_exec      2012-07-27       excellent  Yes    Plixer Scrutinizer NetFlow and sFlow Analyzer 9 Default MySQL Credential
```
