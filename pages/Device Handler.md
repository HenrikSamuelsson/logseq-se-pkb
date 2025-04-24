- Title: Device Handlers in Embedded C
  Tags: #embedded-c #drivers #abstraction #function-pointer #device-handler [[C]]
- 🧩 What Is a Device Handler?
  A device handler is a software construct—often a struct—that provides a standard interface for interacting with a hardware peripheral (e.g., SPI, UART, I2C). It encapsulates driver logic, configuration, and optionally includes callback functions for event handling.
- 💡 Purpose:
	- Abstract away hardware-specific details
	- Provide a clean API to application-level code
	- Enable modularity, reusability, and testability
	- Allow dynamic behaviour via callback function pointers
- 🛠 Typical Structure (SPI Example):
  ```c
  typedef void (*spi_callback_t)(uint8_t data);
  typedef struct {
  	void (*init)(void);
  	void (*write)(uint8_t data);
  	uint8_t (*read)(void);
  	spi_callback_t on_receive; // Function pointer callback
  } spi_driver_t;
  ```
- 📦 Usage:
  ```c
  
  void my_spi_callback(uint8_t data) {
  	// Handle incoming data
  }
  
  spi_driver_t spi = {
  	.init = spi_init_hw,
  	.write = spi_write_hw,
  	.read = spi_read_hw,
  	.on_receive = my_spi_callback
  };
  ```
- In the driver’s ISR:
  ```c
  void spi_isr_handler(spi_driver_t *drv) {
  	uint8_t received = SPI_DATA_REG;
  	if (drv->on_receive) {
  		drv->on_receive(received); // Callback when data received
  	}
  }
  ```
- ## 🧠 Key Benefits:
  * Encapsulation of low-level functionality
  * Event-driven logic via function pointer callbacks
  * Flexibility to swap in different implementations or mock for testing