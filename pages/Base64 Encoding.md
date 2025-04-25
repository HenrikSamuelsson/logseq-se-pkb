Title:: Base64 Encoding in Embedded C
Tags:: [[base64]] [[encoding]] [[embedded-c]] [[data-representation]][[]binary-to-text]]
Source:: [[Embedded Expert's Guide to C]]
title:: Base64 Encoding

- ## 🧱Base64
  Base64 is an encoding scheme that converts binary data into ASCII text, using a fixed 64-character alphabet.
  It's commonly used to:
  * Transmit binary data (e.g. images, firmware) over text-only channels like UART, HTTP, or email.
  * Safely encode binary blobs inside logs, JSON, XML, or other human-readable formats.
- ## 🧠 How Base64 Works
  1. Takes input in 3-byte chunks (24 bits).
  2. Splits those 24 bits into 4 groups of 6 bits.
  3. Each 6-bit value indexes into the Base64 alphabet, `A–Z, a–z, 0–9, +, /`.
  4. Add `=`` padding if input is not a multiple of 3 bytes.
- ## 📉 Base 64 Encoding Example
  Binary: `01001000 01101001 00100001`
  6 bits groups: `010010` `000110` `100100` `100001`
  Corresponding indexes: `18` `6` `36` `33`
  Encoded: `QGfi`
- ## 💻 Code
  Base64 alphabet in a C array
  ```c
  // Base64 alphabet.
  static const char base64_table[] =
  "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/";
  ```
  Encoding function (simplified not handling edge cases or padding), typically wrapped in a loop.
  ```c
  // Encode a single 3-byte block.
  void base64_encode_block(uint8_t input[3], char output[4]) {
  output[0] = base64_table[(input[0] >> 2) & 0x3F];
  output[1] = base64_table[((input[0] & 0x03) << 4) | ((input[1] >> 4) & 0x0F)];
  output[2] = base64_table[((input[1] & 0x0F) << 2) | ((input[2] >> 6) & 0x03)];
  output[3] = base64_table[input[2] & 0x3F];
  }
  ```
- ## ✅ Use Cases Embedded Systems
  * Allows safe transmission over UART, MQTT, HTTP, etc.
  * Can encode firmware chunks for OTA updates.
  * Lets you embed binary sensor logs into JSON or debug output.
- ## ⚠️ Downsides
  * Increases data size by ~33%
  * Adds encoding/decoding overhead (CPU + RAM)