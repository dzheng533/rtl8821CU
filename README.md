首先感谢贡献源代码的朋友。
原英文[README](README.en.md).

## 准备工作
1. 安装依赖工具
```
sudo apt-get install git dkms build-essential raspberrypi-kernel-headers bc
```

2. 克隆代码并调整Makefile

打开根目录的Makefile
为PC环境编译不需要修改跳过此步骤。
如果在树莓派上使用需要调整Makefile 
第一步删除第一行的注解
```
修改前
#EXTRA_CFLAGS += -Wno-error=date-time
修改后
EXTRA_CFLAGS += -Wno-error=date-time
```
第二步修改编译平台
```
修改前
CONFIG_PLATFORM_I386_PC = y
CONFIG_PLATFORM_ARM_RPI = n
CONFIG_PLATFORM_ARM64_RPI = n

修改后
CONFIG_PLATFORM_I386_PC = n
CONFIG_PLATFORM_ARM_RPI = y
CONFIG_PLATFORM_ARM64_RPI = n

如果是64位改这个版本的
CONFIG_PLATFORM_I386_PC = n
CONFIG_PLATFORM_ARM_RPI = n
CONFIG_PLATFORM_ARM64_RPI = y
```

**DKMS** 模式安装执行下面语句:
```
./dkms-install.sh
```
如果需要卸载驱动执行下面语句：
```
./dkms-remove.sh
```