# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/) and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [4.0.0]
### Added
- Support for [installation](https://github.com/Flinesoft/BartyCrouch#installation) via Mint (SwiftSPM based).
- Use [configuration file](https://github.com/Flinesoft/BartyCrouch#configuration) instead of thousands of command line options.
- [Demo project based](https://github.com/Flinesoft/BartyCrouch/tree/stable/Demo/Untouched) integration tests.
- Sophisticated [SwiftGen](https://github.com/SwiftGen/SwiftGen)-Integration (automatic static NSLocalizedString code replacement) via new `transform` option.
### Changed
- All subcommands except `lint` were bundled into the `update` subcommand.
- [Own client implementation](https://github.com/Flinesoft/BartyCrouch/tree/work/big-refactoring/Sources/BartyCrouchTranslator) of updated Microsowft Translator API.
### Deprecated
- None.
### Removed
- The `--override-comments` (`-c`) option on the `code` subcommand is now always turned on, no need to configure.
- The `--extract-loc-strings` (`-e`) option on the `code` subcommand is now always turned on, no need to configure.
### Fixed
- More resilient search behavior (to fix issues such as #64, #87, #102, #105).
### Security
- None.


## [3.13.1]
### Added
- Added ability to ignore empty strings.
  via [#107](https://github.com/Flinesoft/BartyCrouch/pull/107) by [Ludvig Eriksson](https://github.com/ludvigeriksson)
### Changed
- Restructure code for SPM compatibility.
- Introduce CHANGELOG.md, CONTRIBUTION.md and CODE_OF_CONDUCT.md
- Improve Installation section of README
### Deprecated
- None.
### Removed
- None.
### Fixed
- None.
### Security
- None.

## [3.13.0] - 2018-05-09
### Added
– Adds new sub command `lint` with multiple options.
For example you can now add this to your CI service:
```bash
bartycrouch lint -p "/path/to/code/files" -d -e
```
This will:
- [x] fail the CI if duplicate keys are found within the same file (`-d`)
- [x] fail the CI if empty values are found (`-e`)

## [3.12.0] - 2018-05-08
### Added
– Adds new sub command `normalize` with multiple options.
For example you can now add this to your build script:
```bash
bartycrouch normalize -p "/path/to/code/files" -l en -d -w -h -s
```
This will:
- [x] warn against duplicate keys or fix them if it can (`-d`)
- [x] warn against empty values (`-w`)
- [x] make sure your target languages have exactly the same keys as your source language (`-h`)
- [x] sort your keys except for those without translations (`-s`)

## [3.11.2] - 2018-04-16
### Fixed
- Fixed an issue which didn't run sorting keys when no translations were found
- Improved performance with many files

## [3.11.1] - 2018-03-12
### Fixed
- Fixes a bug related to the new `--custom-localizable-name` option.

## [3.11.0] - 2018-03-11
### Added
– Adds new option `--custom-localizable-name` for `code` subcommand

## [3.10.1] - 2018-03-08
### Fixed
- Reverts [#67](https://github.com/Flinesoft/BartyCrouch/issues/67) to fix [#11](https://github.com/Flinesoft/BartyCrouch/issues/11) and [#88](https://github.com/Flinesoft/BartyCrouch/issues/88).

## [3.10.0] - 2018-02-05
### Added
- Add support for Swift Package Manager + fixed some issues.
  Thanks to @mshibanami & @ClementPadovani.

## [3.9.2] - 2018-01-09
### Fixed
Fixes [#72](https://github.com/Flinesoft/BartyCrouch/issues/72).

## [3.9.1] - 2017-12-11
### Fixed
Fixes [#65](https://github.com/Flinesoft/BartyCrouch/issues/65).

## [3.9.0] - 2017-09-26
### Changed
- Update to Swift 4 & Xcode 9
### Fixed
Fixes [#66](https://github.com/Flinesoft/BartyCrouch/issues/66).

## [3.8.1] - 2017-08-02
### Fixed
Fixes [#55](https://github.com/Flinesoft/BartyCrouch/issues/55), [#60](https://github.com/Flinesoft/BartyCrouch/issues/60) and [#63](https://github.com/Flinesoft/BartyCrouch/issues/63).

## [3.8.0] - 2017-05-22
### Added
- Adds new `custom-function` command line option for `code` subcommands. See #25 for details.
  Thanks to @diederich and @crystalstorm for their help to get this done!

## [3.7.1] - 2017-03-28
### Added
- Added compatibility with Xcode 8.3 and Swift 3.1.

## [3.7.0] - 2017-01-20
### Added
- Add new `unstripped` command line option for `interface` and `code` subcommands. See #49.

## [3.6.0] - 2016-12-25
### Added
- Added support for multi-line comments. See #44 for additional details.

## [3.5.0] - 2016-12-14
### Added
Adds two new options to the `code` sub command:
- **extract-loc-strings:** Uses newer tool to extract strings from code. Solves #41.
- Thanks to @fvolchyok for the PR!
- **sort-by-keys:** Sorts the translation entries by their keys. Solves #26.
See also their documentation sections in the README for additional details.

## [3.4.0] - 2016-11-21
### Added
- Adds an option to force update existing comments only via `override-comments` option on the `code` sub command.

## [3.3.0] - 2016-09-22
### Changed
- Updated project to Swift 3 and Xcode 8.

## [3.2.1] - 2016-07-02
### Changed
- Add & configure **SwiftLint linter** and fix all warnings & errors (#28)
### Fixed
- **Better error message** when no `Localizable.strings` file found (#11)
- **Escape double quotes and backslashes** in translated strings (#19)

## [3.2.0] - 2016-06-22
### Added
- Add support for **Objective-C++ '.mm' files** for subcommand `code` (#22)

## [3.1.0] - 2016-06-04
### Added
- **Ignores NSLocalizedStrings** which have ignore constant (e.g. `#bc-ignore!`) in comment (#16)

## [3.0.0] - 2016-05-05
### Added
- **Sub Commands** for updating `interfaces` / `translate` instead of options (like `-t`)
- New sub command to **update `Localizable.strings`** files from `code`
### Changed
- **Streamlined names** of options (force >> override, `-s` >> `-p`)
- **Refactored** quite some code
### Removed
- Input (`-i`), Exclude (`-e`) and Output (`-o`) options

Please have a look at the [migration guide](https://github.com/Flinesoft/BartyCrouch#migration-guides) for a flawless upgrade from version 2.x.


## [2.0.0] - 2016-04-30
### Added
- **Automatic search** for files now also possible **when using `-t`** (translate) via `-s`
### Changed
- Reworked option `-a` (auto) to take a path argument and **renamed to `-s`** (search)
### Fixed
- **Improved build times** when configured with Git root folder path
### Removed
- Translating adds missing keys by default, therefore `-c` option was dropped


## [1.5.0] - 2016-04-08
### Added
- Adds support for **adding missing keys to target translations Strings files** via the `-c` command line option.
  Note that the **undocumented previous behavior** of keeping keys in translation targets that didn't exist in translation source Strings files **was dropped**. From now on only keys that also exist in the source Strings file are kept in the target files to clean up target files. For most projects this change shouldn't have any effect.


## [1.4.0] - 2016-03-14
### Added
- Add support for automatically detecting all Storyboards/XIBs
  Thanks to this change the suggested **build script is now much shorter** and will **automatically adapt** to new Interface Builder file additions. No need to keep the build script updated anymore (for incremental change updates)!

## [1.3.0] - 2016-03-03
### Added
- Add comment Base value update support (only if structure not changed from defaults)
### Changed
- Update actual translation value if same as Base (assuming comment value is previous Base value)
  See #4 for further details on the rationale for the changes made here.


## [1.2.0] - 2016-02-29
### Added
- Add option to use Base localization values when adding new keys

## [1.1.0] - 2016-02-25
### Added
- Add support for automatic machine-translation using Microsoft Translator

## [1.0.0] - 2016-02-25
### Added
- Help messages & more by using [CommandLine](https://github.com/jatoben/CommandLine)
- Shorter argument names (`--input` or `-i`, `--output` or `-o`, `--auto` or `-a`)
- Migration Guide section for major release upgrades in README
### Changed
- Improved error handling and exit codes
- Further internal improvements