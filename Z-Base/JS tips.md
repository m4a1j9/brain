2024.09.15 20:16
Tags: #

# JS tips

Быстрая конвертация rgb в hex
```js
let r = 255; // Red channel (8 bits)
let g = 165; // Green channel (8 bits)
let b = 0;   // Blue channel (8 bits)

// Combine RGB into a single 24-bit integer
let color = (r << 16) | (g << 8) | b;
console.log(color.toString(16)); // Outputs "ffa500" (hex for orange)
```


### Zero-Links
- [[JS performance]]

### Links
- [[00 Tips]]