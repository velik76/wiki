# Table of Contents

- [Table of Contents](#table-of-contents)
  - [Installation](#installation)
  - [rustup](#rustup)
  - [Toolchains](#toolchains)
  - [Additional information](#additional-information)

## Installation

```bash
curl https://sh.rustup.rs -sSf | sh
```

## rustup

| Command                | What for                                                               |
| ---------------------- | ---------------------------------------------------------------------- |
| build                  | Building project. Could be combined with --verbose, --debug, --release |
| clean                  | Cleaning projec                                                        |
| install cargo-binutils | Install binutils                                                       |

## Toolchains

At start install arm toochain:

```bash
sudo apt-get install gcc-arm-none-eabi
```

[Link](https://rust-embedded.github.io/cortex-m-quickstart/cortex_m_quickstart/)

\* thumbv6m-none-eabi
\* thumbv7m-none-eabi
\* thumbv7em-none-eabi
\* thumbv7em-none-eabihf

Figure out the cross compilation target to use:
\* Use thumbv6m-none-eabi for ARM Cortex-M0 and Cortex-M0+
\* Use thumbv7m-none-eabi for ARM Cortex-M3
\* Use thumbv7em-none-eabi for ARM Cortex-M4 and Cortex-M7 (no FPU support)
\* Use thumbv7em-none-eabihf for ARM Cortex-M4F and Cortex-M7F (with FPU support)

## Additional information

| Link                                                                            | Description           |
| ------------------------------------------------------------------------------- | --------------------- |
| [1](https://www.rust-lang.org/what/embedded)                                    | Rust embedded         |
| [2](https://docs.rust-embedded.org/book)                                        | Embedded rust book    |
| [3](https://github.com/rust-embedded/wg)                                        | Some info             |
| [4](https://rurust.github.io/rust_book_ru)                                      | Russian book          |
| [5](https://docs.rust-embedded.org/book/c-tips/index.html)                      | Tipps for C developer |
| [6](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html) | Error handling        |
