# Runtime Lints

[![pub package][pub_badge]][pub_badge_link]
[![License: MIT][license_badge]][license_badge_link]
[![style: very good analysis][badge]][badge_link]

---

This package provides lint + static analysis rules for Dart and Flutter which are used internally on all `open-runtime` repositories which power the [Runtime.Dev platform][runtime_link].

## Inspiration

There are a lot of community driven linting efforts:
* [lints - from dart team][pub_lints]
* [flutter_lints - from dart team][pub_flutter_lints]
* [lint - community driven strict rules][pub_lint]
* [import lint][pub_import_lint]
* [very_good_analysis][pub_very_good_analysis]
* [pedantic - DEPRECATED][pub_pedantic]

## Exploring Linting + Analysis Rules

To learn more about Flutter/Dart linting and understanding what the individual rules mean and
why they exist, check out the [official Dart documentation](https://dart.dev/tools/linter-rules).

You can also look at the [Github Pages hosted version of these linter rules](https://dart-lang.github.io/linter/lints/) 
which offer better experience by pairing easy-to-understand good/bad example snippets that showcase
the rules and their usage.

## Usage

1. To use the lints, add a dependency in your `pubspec.yaml`. Use the Runtime Lints as a dev dependency 
to prevent users of your library from being forced to download `runtime_lints`:

```yaml
dev_dependencies:
  runtime_lints: ^0.1.0
```

2. Set the `include:` in your project's `analysis_options.yaml`. This will ensure you always use the latest version of the linters and analysis rules:

```yaml
include: package:runtime_lints/analysis_options.yaml
```


## Suppressing Lints

There may be cases where specific lint rules are undesirable. Lint rules can be suppressed at the line, file, or project level.

An example use case for suppressing lint rules at the file level is suppressing the `prefer_const_constructors` in order to achieve 100% code coverage. This is due to the fact that const constructors are executed before the tests are run, resulting in no coverage collection.

### Line Level

To suppress a specific lint rule for a specific line of code, use an `ignore` comment directly above the line:

```dart
// ignore: public_member_api_docs
class A {}
```

### File Level

To suppress a specific lint rule of a specific file, use an `ignore_for_file` comment at the top of the file:

```dart
// ignore_for_file: public_member_api_docs

class A {}

class B {}
```

### Project Level

To suppress a specific lint rule for an entire project, modify `analysis_options.yaml`:

```yaml
include: package:runtime_lints/analysis_options.yaml
linter:
  rules:
    public_member_api_docs: false
```

## Badge

To indicate your project is using `runtime_lints` →
[![style: runtime lints][badge]][badge_link]

```md
[![style: runtime lints](https://img.shields.io/badge/style-runtime_lints-B22C89.svg)](https://pub.dev/packages/runtime_lints)
```

[analysis_options_yaml]: https://github.com/open-runtime/runtime_lints/blob/main/analysis_options.yaml
[ci_badge]: https://github.com/open-runtime/runtime_lints/workflows/ci/badge.svg
[ci_badge_link]: https://github.com/open-runtime/runtime_lints/actions
[badge]: https://img.shields.io/badge/style-runtime_lints-B22C89.svg
[badge_link]: https://pub.dev/packages/runtime_lints
[license_badge]: https://img.shields.io/badge/license-MIT-blue.svg
[license_badge_link]: https://opensource.org/licenses/MIT
[ci_badge_link]: https://github.com/open-runtime/runtime_lints/actions
[pub_badge]: https://pub.dev/packages/runtime_lints
[pub_badge_link]: https://pub.dev/packages/runtime_lints

[pub_import_lint]: https://pub.dev/packages/import_lint
[pub_lint]: https://pub.dev/packages/lint
[pub_lints]: https://pub.dev/packages/lints
[pub_flutter_lints]: https://pub.dev/packages/flutter_lints
[pub_pedantic]: https://pub.dev/packages/lints
[pub_very_good_analysis]: https://pub.dartlang.org/packages/very_good_analysis


[open_runtime_github]: https://github.com/open-runtime
[runtime_link]: https://runtime.dev
