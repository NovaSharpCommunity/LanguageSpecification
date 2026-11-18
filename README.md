<img src="https://logo.novasharp.org/lockup/lockup.svg" width="150"/>

# NovaSharp Language Specification

The language specification of NovaSharp.

Current version: **Beta 1.1**.

## About

NovaSharp originated from the beautiful vision of its first creator, who imagined a programming language that would be elegant in form, capable of supporting the unobstructed development of any program, and a pleasure to work with every day.

NovaSharp is a multi-paradigm programming language designed around two goals: **exceptional adaptability** across diverse scenarios, and **high expressiveness**. The entire language — full syntax, full semantics — remains available on bare metal. High-level syntax carries you through low-level work: pointers, manual memory, custom allocators, and ABI-level interoperability are all first-class citizens.

The language is built for experienced programmers. It offers sharp yet obedient tools for the most demanding development scenarios.

## Design Philosophy

- **Operating-system independence**: The full language remains available in bare-metal environments, even after `ExitBootService` has been called.
- **Control returned to the developer**: By default, the compiler reports only syntax errors and static semantic errors.
- **Basic safety at zero cognitive cost**: Basic safety is in effect by default; the programmer writes no annotations and memorizes no additional rules.
- **Explicit semantics**: If the semantics do not contain it, there is no corresponding control flow — no implicit control flow beyond the semantics is permitted.
- **Readability above all**: Syntax is low on abbreviations and shorthands.

## Features

- **Bare-metal to application, one language** — every feature works without an operating system, from firmware to userland.
- **Explicit by design** — dangerous operations require explicit markers; zero semantic ambiguity is a hard design rule.
- **Memory on your terms** — three storage duration, pluggable allocators, and NOLAA object-lifetime analysis, with no borrow checker to appease.
- **Functions as first-class citizens** — created solely by lambdas, with caller and callee conventions cleanly separated.
- **No standard library** — only a mandatory Built-In Library; everything else is yours to define.

## Files

- Language Specification
  - [zh-cn](./docs/specification/zh-cn.md)

## License

Copyright (c) 2026 NovaSharpCommunity.

"NovaSharpCommunity" refers to the GitHub organization at https://github.com/NovaSharpCommunity, its repositories, and their deployed outputs.

"This project" refers to the GitHub repository at https://github.com/NovaSharpCommunity/LanguageSpecification.

This project has been licensed under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0) since Beta 1.1. Please refer to the [LICENSE](/LICENSE) file for details.
