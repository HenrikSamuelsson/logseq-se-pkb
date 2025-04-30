Title:: Command Processor in Embedded Systems
Type:: [[permanent_note]]
Tags:: #embedded-c #command-processor #cli #firmware #uart #function-pointer

- ## 📖 Definition
  
  A **command processor** in embedded systems is a software module that receives, parses, and executes text-based commands, often through a serial interface like UART.
  
  It acts like a lightweight **command-line interface (CLI)** or shell, enabling users or external systems to interact with the device at runtime.
- ## 🧩 Typical Use Cases
- Debugging and diagnostics (e.g., `status`, `mem dump`)
- Runtime configuration (e.g., `set mode 2`)
- Triggering actions (e.g., `reset`, `start log`)
- Accessing internal data for development or calibration
- ## 🔧 Implementation Details
- Accepts input via UART, USB CDC, or another channel
- Stores input in a buffer until a newline or delimiter
- Parses the input string into a **command and arguments**
- Uses a [[dispatch table]] (e.g., with function pointers) to execute the corresponding handler
- ### 🛠 Code Skeleton Example
  
  ```c
  `typedef struct { 
  	const char *cmd;
  	void (*handler)(void); 
  } command_t;
  
  void handle_status(void) {
  	/* show status */ 
  }
  
  void handle_reset(void) {
  	/* reset system */ 
  }
  
  command_t commands[] = {
  	{"status", handle_status}, 
  	{"reset", handle_reset} };
  
  void process_command(const char`* `input) {
  	for (int i = 0; i < sizeof(commands)/sizeof(command_t); i++) {
  		if (strcmp(input, commands[i].cmd) == 0) {
  			commands[i].handler(); 
  			return;
          }
      } 
  }
  
  ```
- ## ✅ Benefits
- Decouples user interface logic from hardware drivers
- Makes embedded firmware more testable and maintainable
- Facilitates field diagnostics without reflashing firmware
- ### ⚠️ Considerations
- Must handle buffer overflows and malformed input
- Should be non-blocking in RTOS environments
- Can grow complex—structure carefully!