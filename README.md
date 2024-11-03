# Windows10-LTSC-2021-21H2-FixPacks

本项目为修复微软官方镜像Windows10-LTSC-2021-21H2的BUG而存在，以方便大家使用。  
由于考虑到已经2024年+++了，不会还有人继续使用32位系统吧？所以只修复了64位的。  
如果你使用的是32位系统请砸了电脑，更换一台支持64位的，哈哈哈！  

- **觉得本项目好一定要记得给俺多点几个星星！！！**

## 问题镜像
文件：SW_DVD9_WIN_ENT_LTSC_2021_64BIT_ChnSimp_MLF_X22-84402.ISO  
大小：4.7GB  
MD5：2579B3865C0591EAD3A2B45AF3CABEEE  
SHA1：C19D7DAFBAFEB26C36E31D97C465E87C7A6E8A4C  
SHA256：C117C5DDBC51F315C739F9321D4907FA50090BA7B48E7E9A2D173D49EF2F73A3  

## 镜像来源
- https://www.hellowindows.cn/

## 存在问题
由于默认官方镜像 Windows10-LTSC-2021-21H2 存在以下BUG：
- 进程wsappx长期占用CPU资源。
- 微软中文输入法不显示候选词。
- 缺少微软应用商店。

## 问题分析
- 查阅得知wsappx是微软应用商店自动更新相关的服务，所以猜测可能是因为LTSC系统中微软精简掉了微软应用商店和UWP应用的相关服务，所以有可能是缺少相应的运行环境，导致wsappx死循环无法正常工作，从而占用大量的CPU资源。
- 对于微软中文输入法不显示候选词的显示问题，当我们进入>微软拼音输入法设置>常规>兼容性中选择使用以前版本的输入法后，输入法显示正常。所以这个显示问题仅仅出现在新版本的输入法上面，而在普通消费者版本的Win10 21H2版本中，输入法并不存在此问题。所以猜测有可能是因为精简版本中精简掉不必要的文件，而导致的bug。
- 通过查阅得知，以上问题都是因为LTSC精简掉了这些软件所需要的VCLibs依赖库，导致部分功能无法实现，于是就出现了bug，所以需要解决此问题仅需要手动安装VCLibs库即可。

## 解决方案
- 输入法和wsappx进程占用资源高均为缺少以下系统组件导致：  
Microsoft.VCLibs.140.00_14.0.30704.0_x64__8wekyb3d8bbwe.Appx

- LTSC系统默认就不带微软商店，所以需要添加以下系统组件：  
Microsoft.NET.Native.Framework.2.2_2.2.29512.0_x64__8wekyb3d8bbwe.Appx  
Microsoft.NET.Native.Runtime.2.2_2.2.28604.0_x64__8wekyb3d8bbwe.Appx
Microsoft.UI.Xaml.2.8_8.2310.30001.0_x64__8wekyb3d8bbwe.Appx
Microsoft.VCLibs.140.00.UWPDesktop_14.0.33519.0_x64__8wekyb3d8bbwe.Appx
Microsoft.VCLibs.140.00_14.0.33519.0_x64__8wekyb3d8bbwe.Appx
Microsoft.WindowsStore_22402.1401.4.0_neutral_~_8wekyb3d8bbwe.Msixbundle

## 使用方法
1.跳转到 Releases 页面，下载对应镜像。  
2.然后和官方镜像安装方式一致即可。  

## 参考网站
- https://github.com/IceLoveYer/LTSC-Add-MicrosoftStore

## 系统展示
![5164142e82b31a92645af5622760ac2](https://github.com/user-attachments/assets/3992f5ff-1c13-47aa-b5a5-b0a59b6d50d0)
![22d7c1ee1d074183ad534ce328bc5bf](https://github.com/user-attachments/assets/76976715-2943-4677-9451-ad52cae3d459)










