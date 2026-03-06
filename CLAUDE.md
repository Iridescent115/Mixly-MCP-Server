# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 语言
与用户交流时使用中文。

## Project Overview

This is a **Mixly 2.0** block-programming project targeting **Arduino AVR (Uno)**. The workflow is:

1. Edit blocks visually in the Mixly 2.0 IDE — this writes `*.mix` files (XML + base64-encoded Arduino source).
2. Mixly exports the compiled Arduino sketch as `*.ino` files.

## File Formats

- **`*.mix`** — Mixly project file. Contains three parts concatenated:
  - `<xml ...>` — Blockly block definitions (the visual program)
  - `<config>` — Board/project configuration JSON
  - `<code>` — Base64-encoded Arduino `.ino` source (the generated code)

- **`*.ino`** — Standard Arduino C++ sketch, generated from the `.mix` file. This is the actual source that gets compiled and flashed to the board.

## Development Notes

- The `.ino` file is **generated** from the `.mix` source. Manual edits to `.ino` will be overwritten by Mixly the next time the project is saved/exported.
- To decode the embedded source from a `.mix` file: extract the content of the `<code>` tag and base64-decode it.
- Target board: `Arduino AVR @ Arduino/Genuino Uno`
