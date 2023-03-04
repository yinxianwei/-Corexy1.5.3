# 首先

拥有一台打印机， 视频教程： https://www.bilibili.com/video/BV15N411o7ou/

# 配置

- vscode + platformio + marlin2.1.x
- MKS_GEN_L_V21
- MKS_TFT_32
- USB打印线

# 下载

```
git clone https://github.com/yinxianwei/dayu-corexy1.5.3.git
cd dayu-corexy1.5.3
git submodule init
git submodule update
```

# marlin修改

### Configuration.h

```
# 主板
#define MOTHERBOARD BOARD_MKS_GEN_L_V21

# 驱动 根据自己的驱动修改对应型号
#define X_DRIVER_TYPE  A4988
#define Y_DRIVER_TYPE  A4988
#define Z_DRIVER_TYPE  A4988
#define Z2_DRIVER_TYPE A4988
#define E0_DRIVER_TYPE A4988


# 热床1个
#define TEMP_SENSOR_BED 1

# 结构
#define COREXY

# 限位开关
#define X_MIN_ENDSTOP_INVERTING true
#define Y_MIN_ENDSTOP_INVERTING true
#define Z_MIN_ENDSTOP_INVERTING true
#define X_MAX_ENDSTOP_INVERTING true
#define Y_MAX_ENDSTOP_INVERTING true
#define Z_MAX_ENDSTOP_INVERTING true

# PID 还会调整
#define DEFAULT_Kp  21.58
#define DEFAULT_Ki   1.50
#define DEFAULT_Kd 77.77

#步进
#define DEFAULT_AXIS_STEPS_PER_UNIT   { 80, 80, 400, 382.166 }

#速率
#define DEFAULT_MAX_FEEDRATE          { 500, 500, 3, 100 }

#电机方向
#define INVERT_X_DIR true
#define INVERT_Z_DIR true

#大小
#define X_BED_SIZE 300
#define Z_MAX_POS 260

#温度
#define PREHEAT_1_TEMP_HOTEND 200
#define PREHEAT_1_TEMP_BED     60

#define SDSUPPORT
#define REPRAP_DISCOUNT_SMART_CONTROLLER

```

## Configuration_adv.h

```
# 双z轴
#define Z_MULTI_ENDSTOPS          // Other Z axes have their own endstops

# TMC2208可开启
#define HYBRID_THRESHOLD
```


## Marlin/src/pins/ramps/pins_RAMPS.h

```
#双z限位开关一个不生效时，修改针脚定义

    #define Z_MIN_PIN                         19
    #define Z_MAX_PIN                         18
```

## 烧录

- usb连接
- vscode打开marlin项目
- 点击Upload