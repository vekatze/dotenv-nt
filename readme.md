# dotenv

`dotenv` is a [Neut](https://vekatze.github.io/neut) library to find env files and load them.

## Installation

```sh
neut get dotenv https://github.com/vekatze/dotenv-nt/raw/main/archive/0-1-39.tar.zst
```

## Types

```neut
// Searches up through the directories to find a file named `env-file-name`
// and loads it as an env file.
define find-and-load-env-file(env-file-name: &string) -> ?unit

// Searches up through the directories to find a file named `env-file-name`.
define find-env-file(env-file-name: &string) -> ?string

// Loads an env file at `path`.
// `initial-buffer-size` is the initial buffer size used when reading the file.
define load-env-file(path: &string, initial-buffer-size: int) -> system(unit)
```

## Example

```neut
import {
  core.environment {get-env},
  core.string.io {print-line},
  this.scene {find-and-load-env-file},
}

define try-dotenv() -> ?unit {
  try _ = find-and-load-env-file(".env");
  try value = get-env("FOO");
  pin value = value;
  print("result: ");
  print-line(value);
  Right(Unit)
}
```
