`sn_entropy_check` calculates the entropy of file(s) by computing a lookup table of the occurrence of the bytes and adding the 
entropy of each byte. The entropy of each byte is defined by the product of the probability of the byte occurring and binary  logarithm of the probability. 

Reference: [Shannon Entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory))

This repository is available as both as a library and a binary. The library provides feature of running the entropy for a single file. 

## Running the binary
To calculate the shannon entropy of a directory you can run:
```shell script
sn_entropy_check <path to dir or file>
```
Note: This will ignore symlinks.

## Using the library
To use the library, create the `Chunk` and call `calculate_entropy()` method on it.

```rust
pub fn entropy() -> Result<(), sn_entropy::Error> {
  let mut file = Chunk::try_new("dummy_file")?;
  let _entropy = file.calculate_entropy();
}
``` 
Entropy of byte slices can be computed by calling `calculate_entropy` function:
```rust
fn entropy() -> f64 {
   let bytes = &[0x00, 0x00, 0x01, 0x01, 0x02]; 
  sn_entropy_check::calculate_entropy(bytes)
}
```

## License

Licensed under the General Public License (GPL), version 3 (LICENSE http://www.gnu.org/licenses/gpl-3.0.en.html).
Linking exception

`sn_entropy_check` is licensed under GPLv3 with linking exception. This means you can link to and use the library from any program, proprietary or open source; paid or gratis. However, if you modify sn_routing, you must distribute the source to your modified version under the terms of the GPLv3.

See the LICENSE file for more details.