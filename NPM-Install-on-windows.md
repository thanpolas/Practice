
This information was current as of May 6th 2016.

## Tips

* On a virtualbox share your working folder so you can manage git and use your editor from osx.

## Install a node.js application on Windows

1. [Install node](https://nodejs.org/)
1. [Install git](https://git-scm.com/download/win)
1. [Install python](https://www.python.org/downloads/windows/) - [2.7.11 x86-64 MSI](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64.msi)
1. Set PYTHON environment variable
    1. Right click on "My Computer" and select "Properties"
    1. Find and select "Advanced system settings"
    1. Find and select "Environment Variables"
    1. On the 'User variables' press the "New..." button
    1. Variable Name: `PYTHON` Value: `C:\python27\python.exe`
    1. Click "OK" all the way back.
1. [Install Visual C++ Build Tools 2015](http://go.microsoft.com/fwlink/?LinkId=691132) - [Complete solution here](https://github.com/nodejs/node-gyp/issues/629#issuecomment-153196245)
    * **IMPORTANT** Choose "Custom Install", and **select both Windows 8.1 and Windows 10 SDKs**.
1. Open CMD and type: `npm config set msvs_version 2015 --global`

You are now ready to perform `npm install` on the project

### Troubleshooting


> e:\app\node_modules\mdns\src\mdns.hpp(32): fatal error C1083: Cannot open include file: 'dns_sd.h': No such file or directory [E:\app\node_modules\mdns\build\dns_sd_bindings.vcxproj]

 To remedy this, download [Bonjour SDK for Windows](https://developer.apple.com/bonjour/).
