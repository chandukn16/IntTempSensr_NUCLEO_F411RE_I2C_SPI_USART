# IntTempSensr_NUCLEO_F411RE_I2C_SPI_USART
NUCLEO-F411RE | Internal Temperature Sensor Acquisition & External Display Interface

This project demonstrates real-time acquisition and telemetry of internal die temperature using the STM32F411RE embedded temperature sensor, with processed output transmitted to external visualization hardware. The internal sensor integrates into the 12-bit SAR ADC subsystem, operating up to 2.4 MSPS, enabling deterministic sampling of the junction temperature. The conversion model uses the device-specific characteristics:
Vref = 3.3 V
ADC resolution = ~0.8 mV/LSB
Typical Temp_Slope ≈ 2.5 mV/°C
Calibrated reference @ 30°C stored in factory memory

🔧 Data Processing Framework
Raw ADC samples are scaled using the ST reference formula:
Temperature (°C) = ((Vsense − V30) / Avg_Slope) + 30
Where Vsense is digitized from channel ADC_IN16.

📡 Display Integration
Measured temperature is formatted in °C and transmitted to external display layers such as a 4-digit LED module, SSD1306 OLED (128×64), or UART terminal. Output refresh cycles operate at 500–1000 ms, maintaining stable readability and thermal tracking.

✔ Firmware Feature Set
🔹 Sensor Acquisition
Internal die sensor enabled on ADC channel 16
Polling / DMA sequence selectable

🔹 Scaler Engine
Floating-point computation
Error compensation and averaging

🔹 Display Drivers
SPI-controlled LED module, multiplexed @ 1 ms digit duty
I2C OLED @ 400 kHz Fast Mode, text + symbol output
USART @ 115200 bps for calibration streaming

✅ Industrial Value
This stack serves as a reusable diagnostic primitive for thermal supervision, embedded validation, predictive maintenance logging, and HMI visualization within automation, wearables, IoT nodes, and instrumentation control systems.
