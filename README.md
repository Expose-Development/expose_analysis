# Expose Analysis

---

This package provides lint rules for Dart and Flutter which are used at [Expose][expose_link].
The package also contains a configuration for [DCM][dcm_link].

## Usage

To use the lints, add as a dev dependency in your `pubspec.yaml`:
Then, add an include in `analysis_options.yaml`:

```yaml
include: package:expose_analysis/analysis_options.yaml
```

This will ensure you always use the latest version of the lints. If you wish to restrict the lint version, specify a version of `analysis_options.yaml` instead:

```yaml
include: package:expose_analysis/analysis_options.1.1.0.yaml
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
include: package:expose_analysis/analysis_options.yaml
linter:
  rules:
    public_member_api_docs: false
```


[expose_link]: https://expose.com.ua
[dcm_link]: https://dcm.dev/