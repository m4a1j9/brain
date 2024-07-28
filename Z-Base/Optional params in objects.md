2022.10.05 23:27
Tags: #z #qt #work 
__
# 00 Optional params in objects
```js
// Will result in ['foo', 'bar']
const items = [
  'foo',
  ...(true ? ['bar'] : []),
  ...(false ? ['falsy'] : []),
]

console.log(items)
```
__
### Zero-Links
- [[00 JS]]
__
### Links
- 