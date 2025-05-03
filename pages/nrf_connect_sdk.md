title:: nrf_connect_sdk
alias:: nRF Connect SDK

- # nRF Connect SDK
- **nRF Connect SDK** is a software development kit used for building wireless applications for the nRF series of microcontrollers developed by [[Nordic Semiconductor]].
- It integrates the [[Zephyr RTOS]], a variety of wireless protocol stacks (such as Bluetooth Low Energy), and [[MCUBoot]] for secure bootloading. The SDK also includes essential middleware, libraries, and drivers for embedded systems development.
- The modular architecture of the SDK simplifies the process of porting applications across different generations of the nRF microcontroller family.
- The [[toolchain]] of the nRF Connect SDK is based on the [[Zephyr toolchain]] with mentionable included tools being:
	- [[Kconfig]]
	- [[Device Tree]]
	- [[CMake]]
	- [[Ninja]]
	- [[GCC]]
- The philosophy behind the architecture is to have high decoupling to support portability and maintainability. With the behaviour off the application being specified in he source code files (`*.c`), the configuration being specified by [[Kconfig]] (`*.conf`), and the hardware  description being placed in the [[Device Tree]] (`*.dts`).
- The philosophy behind the SDK architecture emphasizes strong decoupling to support portability and maintainability. This is achieved by separating concerns:
	- Application behaviour is defined in source code (`*.c` files),
	- Configuration settings are managed via [[Kconfig]] (`*.conf` files),
	- Hardware description is handled using the [[Device Tree]] (`*.dts` files).