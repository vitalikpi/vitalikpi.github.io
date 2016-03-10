---

title: Switch branches without pain

summary: A litttle time saver for switching branches when using IIS locally.

tags: [TFS, IIS, KB]

---

Motivation
----------

As usual, I'll speak about enterprise applications. The common case for me is web application developped using IIS. Intranet applications are usually bound to local IIS server. And this becomes a pain when you need to switch a branch. You need to go to IIS manager, open every web app, click "Basic Settings" and change physical path manually. Looks error-prone. Right?

Solution
--------
To address this issue I have created a small automation script.
The script uses IIS [appcmd tool](http://www.iis.net/learn/get-started/getting-started-with-iis/getting-started-with-appcmdexe) and very straightforward.

Here it is:
``` bat
"%windir%\system32\inetsrv\appcmd" set app "AppName/" -[path='/'].physicalpath:"%CD%\src\AppName"
"%windir%\system32\inetsrv\appcmd" set app "AppName/SubApp" -[path='/'].physicalpath:"%CD%\src\SubApp"
"%windir%\system32\iisreset"
```
