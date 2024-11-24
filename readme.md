# dotenv-nt

`dotenv-nt` is a [Neut](https://vekatze.github.io/neut) library to find env files and load them.

## Installation

```sh
neut get dotenv https://github.com/vekatze/dotenv-nt/raw/main/archive/0-1-8.tar.zst
```

## Types

```neut
// Searches up through the directories to find a file named `env-file-name`
// and loads it as an env file.
define find-and-load-env-file(env-file-name: &text): ?unit

// Searches up through the directories to find a file named `env-file-name`.
define find-env-file(env-file-name: &text): ?text

// Loads an env file at `path`.
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
