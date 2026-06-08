<!--
  SPDX-FileCopyrightText: © 2026 Team CharLS
  SPDX-License-Identifier: BSD-3-Clause
-->

# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) and this project adheres to [Semantic Versioning](http://semver.org/).

## [0.10.0 - 2026-06-08]

### Changed

- Updated dependencies to the latest versions.

## [0.9.0 - 2026-04-03]

### Added

- CI pipeline to publish package from GitHub.

### Changed

- Updated dependencies to the latest versions.


## [0.8.0 - 2026-01-31]

### Added

- Initial release, based on https://github.com/chafey/charls-js

### Changed

- Applied StandardJS code style throughout the entire codebase (src/*, test/*, all JavaScript files).
- Switched to ES6 module system.
- Updated WASM to v3.0.
- Replaced emscripten bind generated JS code with adapters that call the C API of CharLS.

### Fixed

- Enabled native WASM exceptions. This allows CharLS to correctly report errors to the calling JS code.
- Corrected JavaScript code examples in documentation to follow StandardJS conventions.
