![](../../workflows/gds/badge.svg) ![](../../workflows/docs/badge.svg) ![](../../workflows/test/badge.svg) ![](../../workflows/fpga/badge.svg)

# Tiny Tapeout Verilog Project Template
A variant for the [Verilog Meetup](https://verilog-meetup.com) community

![The corresponding FPGA board setup](https://github.com/yuri-panchul/ttsky-verilog-template-for-verilog-meetup/blob/main/docs/tang_nano_9k_fpga_board_setup.jpg)

This template has the following changes on the top of the base `ttsky-verilog-template`.

1. It instantiates [lab_top](https://github.com/yuri-panchul/basics-graphics-music/blob/main/book/10_moving_graphics/lab_top.sv)
module inside [project.v](https://github.com/yuri-panchul/ttsky-verilog-template-for-verilog-meetup/blob/main/src/project.v).
`lab_top` is used to abstract FPGA boards in [BGM a.k.a. basics-graphics-music](https://github.com/yuri-panchul/basics-graphics-music/tree/main) project.

2. Instantiates and adds glue logic for the [controller of the TM1638 board interface](https://github.com/yuri-panchul/basics-graphics-music/blob/main/peripherals/tm1638_board.sv).
This peripheral board features 8 buttons, 8 LEDs and 8-digit 7-segment indicator.
It is used in BGM project as an add-on for FPGA boards that have insufficient number of LEDs/buttons/7-segment digits for the lab examples in BGM package.

3. Adds glue logic to make the design compatible with [Tiny VGA](https://github.com/mole99/tiny-vga)
used in [TT10 Demoscene](https://tinytapeout.com/competitions/demoscene-tt10) projects.

4. Instantiates and adds glue logic for the [controller of the I2S interface for the INMP441 microphone](https://github.com/yuri-panchul/basics-graphics-music/blob/main/peripherals/inmp441_mic_i2s_receiver.sv).

5. Adds some code to bypass Python-based cocotb testbench and do all verification in SystemVerilog.

6. Adds hooks to the documentation and other text files to make use of the template easier. Just grep for `TODO`.

## Credits

Yuri Panchul and [Verilog Meetup](https://verilog-meetup.com), with contributions from:

* TM1638 interface module support, based on Alan Garfield's implementation: Alexander Kirichenko, Ruslan Zalata and Anton Malakhov.

* Sound recognition with INMP441 microphone: Victor Prutyanov and Vadim Ostrikov.

* Other contributors to the [basics-graphics-music (BGM)](https://github.com/yuri-panchul/basics-graphics-music) project.

Below is the original text from the Tiny Tapeout GitHub repository.

# Tiny Tapeout Verilog Project Template

- [Read the documentation for project](docs/info.md)

## What is Tiny Tapeout?

Tiny Tapeout is an educational project that aims to make it easier and cheaper than ever to get your digital and analog designs manufactured on a real chip.

To learn more and get started, visit https://tinytapeout.com.

## Set up your Verilog project

1. Add your Verilog files to the `src` folder.
2. Edit the [info.yaml](info.yaml) and update information about your project, paying special attention to the `source_files` and `top_module` properties. If you are upgrading an existing Tiny Tapeout project, check out our [online info.yaml migration tool](https://tinytapeout.github.io/tt-yaml-upgrade-tool/).
3. Edit [docs/info.md](docs/info.md) and add a description of your project.
4. Adapt the testbench to your design. See [test/README.md](test/README.md) for more information.

The GitHub action will automatically build the ASIC files using [LibreLane](https://www.zerotoasiccourse.com/terminology/librelane/).

## Enable GitHub actions to build the results page

- [Enabling GitHub Pages](https://tinytapeout.com/faq/#my-github-action-is-failing-on-the-pages-part)

## Resources

- [FAQ](https://tinytapeout.com/faq/)
- [Digital design lessons](https://tinytapeout.com/digital_design/)
- [Learn how semiconductors work](https://tinytapeout.com/siliwiz/)
- [Join the community](https://tinytapeout.com/discord)
- [Build your design locally](https://www.tinytapeout.com/guides/local-hardening/)

## What next?

- [Submit your design to the next shuttle](https://app.tinytapeout.com/).
- Edit [this README](README.md) and explain your design, how it works, and how to test it.
- Share your project on your social network of choice:
  - LinkedIn [#tinytapeout](https://www.linkedin.com/search/results/content/?keywords=%23tinytapeout) [@TinyTapeout](https://www.linkedin.com/company/100708654/)
  - Mastodon [#tinytapeout](https://chaos.social/tags/tinytapeout) [@matthewvenn](https://chaos.social/@matthewvenn)
  - X (formerly Twitter) [#tinytapeout](https://twitter.com/hashtag/tinytapeout) [@tinytapeout](https://twitter.com/tinytapeout)
  - Bluesky [@tinytapeout.com](https://bsky.app/profile/tinytapeout.com)
