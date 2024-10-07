# dotenv-nt

`dotenv-nt` is a [Neut](https://vekatze.github.io/neut) library to find env files and load them.

## Installation

```sh
neut get dotenv https://github.com/vekatze/dotenv-nt/raw/main/archive/0-1-3.tar.zst
```

## Types

```neut
define find-and-load-env-file(env-file-name: &text): ?unit

define find-env-file(env-file-name: &text): ?text

define load-env-file(path: &text, initial-buffer-size: int): system(unit)
```

## Example

```neut
import {
  core.environment {get-env},
  dotenv.scene {find-and-load-env-file},
}

define try-dotenv(): ?unit {
  try _ = find-and-load-env-file(".env") in
  try value = get-env("FOO") in
  printf("result: {}\n", [value]);
  Right(Unit)
}
```
