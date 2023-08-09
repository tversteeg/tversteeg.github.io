+++
title = "Evolution of Castle Game: A Decade of Experimentation"
date = 2023-08-08
description = "A history of the experiments that led to the current iteration of castle-game."
draft = true

[taxonomies]
tags = ["rust", "gamedev"]
+++

Welcome to a technical deep-dive into the evolution of [Castle Game](https://github.com/tversteeg/castle-game), a project that has spanned a decade of experimentation and development.
In this post, I'll explore the technical trajectory that has brought me to the current state of the game, delving into the iterations, challenges, and lessons learned along the way.

<!-- more -->

This journey nicely overlaps with my other journey of learning the Rust programming language.

## Prelude

This story takes root in my formative years, when I was growing up and experimenting with the possibilities of Macromedia Flash to create animations and Flash games.

After figuring out that you can adjust the pixels of sprites in Flash I became infatuated with visual effects based on this effect and also using it in combination with physics engines which I also was very interested by.

## The Beginning (2010)

The concept of Castle Game took root in 2010, with a focus on environmental destruction as a core gameplay mechanic.

This led me to adopt a 2D side view approach, with an entirely black backdrop and characters manifested as small black sprites contrasted against a vibrant orange canvas.

## First Implementation (2018)

As my proficiency with Rust grew, so did my desire to create a game with it.

I started out with creating a framebuffer with the [minifb](https://github.com/emoon/rust_minifb) crate.

I quickly got working on it, rendering a background.

Simultaneously, I began integrating an Entity-Component-System called [specs](https://github.com/amethyst/specs).
While its potential was significant and the crate's implementation great, the structure an ECS forced on the game contributed to my eventual decision to set aside the efforts of continuing the game, for now...

## The Bevy Detour (2022)

In 2022, I explored the Bevy game engine, driven by its growing popularity and reputation.

I pivoted to a vector art style approach, inspired by [Mike Mezhenin's Ludum Dare 46 entry](https://mike-mezhenin.itch.io/keep-calm), departing from pixel-art.
My art skills didn't improve much so I wanted to keep it simple and this still seemed a perfect fit for that while still being pretty.
The tool I used to make the images was Inkscape.

The thing I liked about Bevy is how many systems and libraries were already available to seamlessy combine together, reducing a lot of reinventing the wheel.
But I quickly walked against the same ECS wall as my earlier attempts.
I guess ECS is not for me.

This iteration also led me to work with some interesting technologies:

- An SVG-to-mesh converter
- An algorithm that procedurally splits rigid body rocks based on forces applied

## Latest Iteration (2023)

Today, in 2023, Castle Game is undergoing its latest rewrite.
Before delving into the rewrite, significant enhancements were made to the [blit](https://github.com/tversteeg/blit) crate, addressing performance and usability concerns.

I started this latest iteration because the initial itch still hasn't been scratched properly yet.

For the art style I went back to pixel-art but this time keeping the form and aesthetics of the vector art style.

I'm trying to keep the code and the datastructures simple and clear, holding myself back a lot to not pre-maturily optimize everything.

Of course this couldn't be another iteration without a new technical challenge.
This time it's writing a physics engine.
While developing the game I got inspired by the [starframe](https://github.com/m0lentum/starframe) Rust game engine, I saw that it used [Extended Position-Based Dynamics](https://matthias-research.github.io/pages/publications/PBDBodies.pdf), a physics system that I never heard of before.
I checked it out and it seemed very elegant and not that hard to implement.
For the broad-phase collision detection I created a simple Spatial Hash Grid with a fixed bucket size.
I'm not entirely happy with how it works for now but it does the trick.
For the narrow-phase collision detection I first tried using my own Separating Axis Theorem implementation but I quickly got stuck trying to find multiple contact points, so instead I went for the [parry2d](https://docs.rs/parry2d/latest/parry2d/) crate.

Another major improvement is the [assets_manager](https://github.com/a1phyr/assets_manager) crate I've integrated.
This allows for hot-reloading of assets, which saves a tremendous amount of time with tweaking variables and waiting for re-compiles.

## Lessons and Future Prospects

The journey of Castle Game has been one of experimentation and technical growth. Lessons have been learned through each iteration, shedding light on the most effective tools, frameworks, and architectural choices.
The evolution continues as I refine the project and anticipate its future direction.

## Stay Tuned

Keep an eye on the Castle Game repository for further updates on its technical evolution. Your interest and support are integral to the ongoing development of this project.
