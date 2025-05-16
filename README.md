# STM32 BJT Tester

STM32-based bipolar junction transistor (BJT) tester that automatically:

- Detects the presence of a BJT
- Determines its type (NPN or PNP)
- Identifies pin configuration (EBC or CBE)
- Calculates static gain (βs) and active gain (βa)

Results are displayed on an I2C-driven LCD and logged via UART.

---

## 📋 Features

- **Transistor Detection**  
  Compares collector-emitter voltage difference against a threshold to verify BJT presence.

- **Type Identification**  
  If V(C) > V(E) → NPN; otherwise → PNP.

- **Pin Configuration (EBC/CBE)**  
  Measures two voltage differences (Δ1, Δ2) after re-routing pins;  
  Δ1 > Δ2 → CBE, Δ1 ≤ Δ2 → EBC.

- **Static Gain (βs)**  
  Ic = |ADC_collector – full_scale|, Ib = |ADC_base – full_scale| → βs = Ic / Ib.

- **Active Gain (βa)**  
  Measured over 10 cycles in a timed loop; values updated on LCD and sent over UART.

- **User Interface**  
  - I2C LCD display for real-time feedback  
  - UART2 at 115200 baud for detailed serial output

- **Easy Setup**  
  Ready-to-import STM32CubeIDE project with HAL drivers configured.

---

## ⚙️ Hardware Requirements

- STM32 microcontroller (e.g., Nucleo board) with ADC & PWM support  
- GPIO pins PA6 & PA7 for transistor switching  
- ADC channels: PA0 (collector), PA1 (base), PB0/ADC8 (emitter)  
- I2C-driven LCD module  
- UART2 (TX/RX) connection  
- Stable 3.3 V or 5 V power supply  
- BJT test socket

---

