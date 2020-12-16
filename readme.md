# pb-clang-format

A place to store our common clang-format binaries,
and related things.

## Using as Meson subproject

First, add a file called `subprojects/pb-clang-format.wrap`:
```ini
[wrap-git]
directory=pb-clang-format
url=https://github.com/PacificBiosciences/pb-clang-format.git
revision=main

[provide]
program_names = tools/check-formatting
```

In your `meson.build`:
```py
if (not meson.is_subproject())
  pbcf_check_formatting = find_program('tools/check-formatting', 'subprojects/pb-clang-format/tools/check-formatting', required : true)
endif
```
And:
```py
subproject('pb-clang-format')
```

## Testing

```sh
cd test-pbcf
make clean
make
make clean
```
