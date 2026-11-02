# Yuyi A2 LCD1306 Wheeled Robot

Yuyi (语翼) A2 主板 + SSD1306 128x64 OLED 的 AI 语音双轮/履带车板卡，
从厂商 2026-06-03 源码包（xiaozhi-esp32 v2.0.2）移植到 xiaozhi-esp32 v2.5.3。

## 硬件

- 主控：ESP32-S3
- 音频：ES8311 + ES7210（BoxAudioCodec）
  - I2S：MCLK 40 / WS 45 / BCLK 39 / DIN 21 / DOUT 48
  - I2C：SDA 38 / SCL 47，PA 46
- 屏幕：SSD1306 OLED 128x64（I2C，SDA 15 / SCL 16，地址 0x3C）
- 电机：双轮差速，LEDC PWM，左电机 IO 9/11，右电机 IO 13/14
- 按键：BOOT 1 / 音量+ 18 / 音量- 2；LED 17
- 电池：ADC 3（分压 1:2），充电检测 41 / 充满 42
- 灯光传感器：UART 12/13

## 语音控制工具（MCP）

- self.tank.forward / backward / turn_left / turn_right（5 秒后自动停）
- self.tank.dance / self.tank.stop

## 编译

```bash
python scripts/build.py yuyi/a2-lcd1306 --name yuyi-a2-lcd1306
```

烧录前确认 `sdkconfig` 中 `CONFIG_BOARD_TYPE_YUYI_A2_LCD1306=y`。

## 备注

- 电池为 1:2 分压，电量按 3.0V–4.2V 折算。
- JD9853 SPI LCD 240x296 变体（原厂 yuyi_a2_v1）尚未移植，等确认新设备屏幕型号后再加。
