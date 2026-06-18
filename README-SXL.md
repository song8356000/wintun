1.基础环境
     win10环境下vs2022，SDK26100，amd64（windows-x64）环境
2.驱动程序环境配置
  2.1  启动Windows PowerShell(管理员)，执行：winget search WDK，查看WDK版本，如下所示
		PS C:\WINDOWS\system32> winget search WDK
		名称                                         ID                              版本            匹配           源
		------------------------------------------------------------------------------------------------------------------
		Windows Driver Kit                           Microsoft.WindowsWDK.10.0.19041 10.1.19041.685                 winget
		Windows Driver Kit - Windows 10.1.22000.1    Microsoft.WindowsWDK.10.0.22000 10.1.22000.1                   winget
		Windows Driver Kit - Windows 10.0.22621.2428 Microsoft.WindowsWDK.10.0.22621 10.1.22621.2428                winget
		Windows Driver Kit - Windows 10.0.26100.6584 Microsoft.WindowsWDK.10.0.26100 10.1.26100.6584                winget
		Windows Driver Kit - Windows 10.0.28000.1839 Microsoft.WindowsWDK.10.0.28000 10.1.28000.1839                winget
		HexChat                                      HexChat.HexChat                 2.16.2          Tag: xchat-wdk winget
   2.2  执行：winget install Microsoft.WindowsWDK.10.0.26100，等待安装成功
3.修改wintun.props文件
   将<TargetVersion>Windows7</TargetVersion>这行修改为<TargetVersion>Windows10</TargetVersion>，在此行下面添加
   <KmdfVersion>1.15</KmdfVersion>
   Windows 7 时代配套的 KMDF（内核模式驱动框架）版本是 1.9。而现代 Windows 10/11 使用的是 1.15 到 1.33 以上，这里修改为1.15
4.清理，重新生成即可