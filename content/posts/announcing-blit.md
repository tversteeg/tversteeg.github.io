+++
title = "Announcing Rust library: blit"
date = 2020-01-06
[taxonomies]
tags = ["rust", "gamedev", "sprite", "pixels"]
+++

[Blit](https://github.com/tversteeg/blit) is a library I started developing.

It's part of a set of tools that can be used to create game engines.

It allows you to draw images to another image buffer with a mask (["blitting"](https://en.wikipedia.org/wiki/Bit_blit)) as you can see in this example:

![Example](https://raw.githubusercontent.com/tversteeg/blit/master/img/example.png)

The left smiley is the source image, the pink background is the mask. The right smiley is another instance of the image "blitted" on top of it, masking all the pink pixels out.

This is all done using software rendering so the library should work on all platforms.

Future optimization features I wish to add include:
- SIMD support
- OpenCL support

[source code](https://github.com/tversteeg/blit)

[documentation](https://docs.rs/blit)
