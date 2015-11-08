# strfile-rs 0.1.0
![crates.io badge](https://img.shields.io/crates/v/strfile.svg) ![TravisCI badge](https://travis-ci.org/lensvol/strfile-rs.svg)

Tiny crate for reading `strfile` headers, which are indexed representations of quote files used in `fortune` utility. 

It is a hobby project, so pull requests are welcome. :)

## Usage

```rust
extern crate strfile;

use strfile::Strfile;

fn display_strfile_header(header: &Strfile) {
    println!("Version:\t{}", header.version);
    println!("Strings:\t{}", header.number_of_strings);
    println!("Longest:\t{}", header.longest_length);
    println!("Shortest:\t{}", header.shortest_length);
    println!("Delimeter:\t{:?}", header.delim as char);

    println!("Randomized:\t{}", header.is_random());
    println!("Ordered:\t{}", header.is_ordered());
    println!("ROT13:\t\t{}", header.is_rotated());
    println!("Comments:\t{}\n", header.has_comments());
}   

let header = Strfile::parse("quotes.dat").unwrap();
let quotes = h.read_quotes(quotes_fn).unwrap();

println!("{:?}", header);
```

## TODO

* Support for headers generated on 64-bit machines
* Construct headers from raw quotes file
* Partial modification of headers (randomization of offsets, "encrypting" etc)

