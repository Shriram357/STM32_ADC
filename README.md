# STM32_ADC
Implemented a 100 Hz hardware-timed ADC system on STM32F303RE using TIM2 TRGO. ADC conversions are DMA-driven and interrupt-handled, with results transmitted via USART2 (ST-LINK VCP) and displayed on a serial terminal, ensuring deterministic sampling and low CPU overhead.
