本patch兼容全部nongki内核，gki内核自测。
打入此patch会开启驱动模块相关验证，无需额外在内核配置文件补充模块签名相关的属性
若配置文件中默认已有，请直接删除掉相关行保存后再执行生成配置文件或编译步骤，不要直接改n！否则不会起作用！

**主要功能实现**

在模块签名开启状态下，检测到用户非法的加载/安装第三方未签名模块，强行阻止并在用户执行的终端中输出自定义提示信息（可修改patch内提示信息的内容）
提示信息也会被记录到内核日志中

**提示**
module_sig.patch为自动开启签名相关属性，module_sig_nonKconfig.patch相反，其余功能保持不变，如第一个报错请打第二个，并手动在defconfig中开启CONFIG_MODULE_SIG相关选项

例子
CONFIG_MODULE_SIG=y
CONFIG_MODULE_SIG_ALL=y
