# WINE下安装微信
## 安装WINE
- sudo apt install wine
## 安装winetricks
- sudo apt install winetricks
## 配置32位的wine prefix
1. 删除home文件夹下现有的.wine文件夹（这个文件夹是64位的设置）
2. 终端执行 WINEPREFIX="$HOME/.wine" WINEARCH=win32 wine wineboot建立新的32位prefix
## 配置wine
- 终端键入winecfg， 在graphics中调整dpi， 在applications-windows version选择win10
## 安装依赖项
- 终端键入winetricks
  - select the default wineprefix-OK
  - install a windows dll or component-OK
  - 勾选riched20\riched30\richtx32
  - 如果遇到依赖文件下载失败，在本目录missed file中赋值相应文件替换即可
## 安装字体
- 终端键入winetricks
  - select the default wineprefix-OK
  - install a font-OK
    - 勾选wenquanyi和fake chinese后点击ok
    - 或者cd到该文件夹下，终端键入wine regedit set_font.reg
- 参考了 https://blog.csdn.net/mhlwsk/article/details/51919916
## 安装微信
- 下载最新版微信exe安装程序
- 终端键入wine uninstaller, install中选择安装程序后安装
- 安装完之后桌面会出现微信快捷方式(.desktop文件)，打开成文本，在Exec=env后加入LANG=zh_CN.UTF-8参数，强制微信运行的语言环境为中文，避免乱码显示。修改过后立即生效
- dash里面（即按下win键显示的软件图标）也会出现wechat快捷方式，对应的.desktop文件在$Home/.local/share/applications/wine/Programs/WeChat文件夹下。（在home文件夹下直接搜索文件名即可找到），也按照上一条进行修改。不过这里修改后要重启之后才会生效

-至此完成安装，双击桌面快捷方式运行即可！！！