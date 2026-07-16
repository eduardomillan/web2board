# Changelog

All notable changes to web2board are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/),
and this project adheres to [Semantic Versioning](https://semver.org/).

## [3.0.1] - 2026-07-16

### Fixed
- **Console traceback when no board is connected.** `SerialMonitorHub.find_board_port`
  previously let a `CompilerException` ("No port found, check the board: \"...\" is connected")
  escape from the asynchronous task, printing an unhandled error in the web2board
  console. It now catches the exception and returns a structured `BOARD_NOT_READY`
  reply, so the client shows the existing "No board was detected" warning instead of
  a stack trace.
- **Crash-prone port listing.** `SerialMonitorHub.get_available_ports` now returns an
  empty list when the compiler/uploader cannot be constructed, instead of propagating
  an exception through an asynchronous task.

## [3.0.0] - previous release
- See the web2board-v3.0.0 release notes.

[3.0.1]: https://github.com/eduardomillan/web2board/releases/tag/web2board-v3.0.1
[3.0.0]: https://github.com/eduardomillan/web2board/releases/tag/web2board-v3.0.0
