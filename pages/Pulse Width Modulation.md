Title:: pulse_width_modulation
  Alias:: PWM
  Type:: [[permanent_note]]
  Created:: [[2025-05-11]]
  Tags:: [[Embedded C]] [[GPIO]] [[signal_generation]] [[motor_control]] [[actuator]] 
  Source:: [[Embedded Systems Architecture]]

	- ## Main Idea  
	  *Write a clear, concise summary of the idea or concept in your own words.*
	- ## Details  
	  *Add definitions, background, or relevant context here.*
	- ## Code Example (if any)  
	  ```c
	  // Add your example code here
	  ```
	- ## Implications / Insights
		- Why does this matter? What should be done differently based on this?
	- Prevention / Best Practices
		- Bullet-point practical advice
	- ## See also
		- [[Related Concept 1]]
		- [[Related Concept 2]]
- # Pulse Width Modulation
- ## Definition
- *Pulse width modulation* (PWM) is a technique used to encode a value into the **width (duration)** of digital pulses in a periodic signal.
- A **microcontroller's GPIO** pin can be configured to output a square wave where the **high time** (pulse width) varies, while the **period** remains constant.
- ## Implementation
- The naïve way to implement PWM in software using loops, but since this approach will make it hard to also have the CPU perform other tasks a better option is to rely on a [[timer]] [[peripheral]] commonly part of microcontrollers.