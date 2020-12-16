project(
  'pb-clang-format',
  version : '0.0.1',
  license : 'BSD-3',
  meson_version : '>= 0.53.0')

#pbcf_dep = dependency('pb-clang-format', fallback : ['pb-clang-format', 'pbcf_dep'], required : true)
subproject('pb-clang-format')

if (not meson.is_subproject())
  pbcf_check_formatting = find_program('tools/check-formatting', 'subprojects/pb-clang-format/tools/check-formatting', required : true)
endif
