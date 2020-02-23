+++
title = "Announcing Rust library: specs-blit"
date = 2019-12-29
[taxonomies]
tags = ["rust", "gamedev", "sprite", "pixels", "specs"]
+++

[Specs-blit](https://github.com/tversteeg/specs-blit) is a library I started developing.

It's part of a set of tools that can be used to create game engines.

The library exposes the [blit](@/posts/announcing-blit.md) functionality in [specs](https://specs.amethyst.rs/).
It allows you to create `Sprite` components that can be positioned and rendered to a `PixelBuffer`.
The sprites are all put on the heap and passed around as references.

[source code](https://github.com/tversteeg/specs-blit)

[documentation](https://docs.rs/specs-blit)
