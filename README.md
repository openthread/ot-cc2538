[![Build][ot-gh-action-build-svg]][ot-gh-action-build]

[ot-gh-action-build]: https://github.com/openthread/ot-cc2538/actions?query=workflow%3ABuild+branch%3Amain+event%3Apush
[ot-gh-action-build-svg]: https://github.com/openthread/ot-cc2538/workflows/Build/badge.svg?branch=main&event=push

---

# OpenThread on CC2538 Example

This repo contains example platform drivers for the [Texas Instruments CC2538][cc2538].

[cc2538]: http://www.ti.com/product/CC2538

The example platform drivers are intended to present the minimal code necessary to support OpenThread. As a result, the example platform drivers do not necessarily highlight the platform's full capabilities.

## Toolchain

Download and install the [GNU toolchain for ARM Cortex-M][gnu-toolchain].

[gnu-toolchain]: https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm

In a Bash terminal, follow these instructions to install the GNU toolchain and other dependencies.

```bash
$ cd <path-to-ot-cc2538>
$ ./script/bootstrap
```

## Building

In a Bash terminal, follow these instructions to build the cc2538 examples.

```bash
$ cd <path-to-ot-cc2538>
$ ./script/build
```

## Flash Binaries

If the build completed successfully, the `elf` files may be found in `<path-to-cc2538>/build/bin/`.

To flash the images with [Flash Programmer 2][ti-flash-programmer-2], the files must have the `*.elf` extension.

```bash
$ cd <path-to-cc2538>/build/bin/cli/ot-cli-ftd
$ cp ot-cli-ftd ot-cli-ftd.elf
```

To load the images with the [serial bootloader][ti-cc2538-bootloader], the images must be converted to `bin`. This is done using `arm-none-eabi-objcopy`

```bash
$ cd <path-to-cc2538>/build/bin/cli/ot-cli-ftd
$ arm-none-eabi-objcopy -O binary ot-cli-ftd ot-cli-ftd.bin
```

The [cc2538-bsl.py script][cc2538-bsl-tool] provides a convenient method for flashing a CC2538 via the UART. To enter the bootloader backdoor for flashing, hold down SELECT for CC2538DK (corresponds to logic '0') while you press the Reset button.

[ti-flash-programmer-2]: http://www.ti.com/tool/flash-programmer
[ti-cc2538-bootloader]: http://www.ti.com/lit/an/swra466a/swra466a.pdf
[cc2538-bsl-tool]: https://github.com/JelmerT/cc2538-bsl

## Interact

1. Open terminal to `/dev/ttyUSB1` (serial port settings: 115200 8-N-1).
2. Type `help` for list of commands.
3. See [OpenThread CLI Reference README.md][cli] to learn more.

[cli]: https://github.com/openthread/openthread/blob/main/src/cli/README.md

# Contributing

We would love for you to contribute to OpenThread and help make it even better than it is today! See our [Contributing Guidelines](https://github.com/openthread/openthread/blob/main/CONTRIBUTING.md) for more information.

Contributors are required to abide by our [Code of Conduct](https://github.com/openthread/openthread/blob/main/CODE_OF_CONDUCT.md) and [Coding Conventions and Style Guide](https://github.com/openthread/openthread/blob/main/STYLE_GUIDE.md).

# License

OpenThread is released under the [BSD 3-Clause license](https://github.com/openthread/ot-cc2538/blob/main/LICENSE). See the [`LICENSE`](https://github.com/openthread/ot-cc2538/blob/main/LICENSE) file for more information.

Please only use the OpenThread name and marks when accurately referencing this software distribution. Do not use the marks in a way that suggests you are endorsed by or otherwise affiliated with Nest, Google, or The Thread Group.

# Need help?

There are numerous avenues for OpenThread support:

- Bugs and feature requests — [submit to the Issue Tracker](https://github.com/openthread/openthread/issues)
- Stack Overflow — [post questions using the `openthread` tag](http://stackoverflow.com/questions/tagged/openthread)
- Google Groups — [discussion and announcements at openthread-users](https://groups.google.com/forum/#!forum/openthread-users)

The openthread-users Google Group is the recommended place for users to discuss OpenThread and interact directly with the OpenThread team.
