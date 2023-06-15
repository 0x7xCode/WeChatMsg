# WeChatMsg
微信聊天记录dump解密

### 1.0   2020-06-19
  通过Version.dll 劫持 WeChat.exe
  并通过特征 

```pascal
($44, $42, $46, $61, $63, $74, $6F, $72, $79, $3A, $3A, $65, $6E, $63, $72, $79, $70, $74, $44, $42) 
```

 找到函数入口并Hook

```pascal
Function Func_Dst(Args1, Args2, Args3 :PPointer):Pointer; Stdcall;
```

  Arg1^ 为数据库名， Arg3^ 为数据库解密Key

### 2.0   2021-03-09
  通过打开WeChat.exe进程并定位到模块WeChatWin.dll，将DLL模块内存整个读取并通过AobScan找出加密Key并读取

### 2.5   2021-04-15
  通过打开WeChat.exe进程并定位到模块WeChatWin.dll，将DLL模块内存整个读取并通过AobScan找到神奇的函数地址，并使用反汇编引擎（BeaEngine）取出寄存器中加密Key的存放地址。 至此开始版本通杀之路

### 2.6   2021-04-20
  添加MiniZip自动打包

### 2.7   2021-08-13
  加入对绿色版和修改版（包括魔改版）PC微信的支持

### 3.0   2023-06-14

  由于PC微信更新所有文件从x86升级为x64，更新增加对x64的支持。通过PEB遍历遍历模块，并使用NtWow64ReadVirtualMemory64（32位Beacon时，64位用ReadProcessMemory）读取内存

  

![](11111111)

