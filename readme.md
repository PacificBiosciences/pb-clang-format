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
pbcf_dep = dependency('pb-clang-format', fallback : ['pb-clang-format', 'pbcf_dep'], required : true)

if (not meson.is_subproject())
  pbcf_check_formatting = find_program('tools/check-formatting', 'subprojects/pb-clang-format/tools/check-formatting', required : true)
endif
```
