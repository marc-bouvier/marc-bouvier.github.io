---
title: Using keepass2 with google sync plugin and Ubuntu 18.4
tags : How-To
---

* Prerequisite : having already create a kdbx database and synced it google drive from Windows 10 
* First [install keepass 2](http://ubuntuhandbook.org/index.php/2017/06/install-keepass-2-36-via-ppa-in-ubuntu-16-04-14-04-17-04/)
* Then download the latest version of [Google Sync plugin](https://keepass.info/plugins.html#kpgsync)
* Extraxt and copy `GoogleSyncPlugin.plgx` to `/usr/lib/keepass2` side by side with Keepass.exe
* Download log4net from `https://logging.apache.org/log4net/download_log4net.cgi`
* Extract and copy `path_to_extracted_archive/log4net-2.0.8/bin/mono/4.0/release/log4net.dll` to `/usr/lib/keepass2` side by side with Keepass.exe
* On windows 10 get `System.ServiceModel.Web.dll` from `C:\Windows\Microsoft.NET\Framework\v4.0.30319\System.ServiceModel.Web.dll`.
* Copy `System.ServiceModel.Web.dll` to `/usr/lib/keepass2` side by side with Keepass.exe
* You can now run keepass2 and sync with google drive!

If you have trouble you can follow the thread on sourceforge : https://sourceforge.net/p/kp-googlesync/discussion/general/thread/19cca399/

