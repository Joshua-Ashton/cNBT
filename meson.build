project('cNBT', ['c'], version : '0.0', meson_version : '>= 0.55', default_options : [
  'warning_level=3'
])

cnbt_compiler = meson.get_compiler('c')
cnbt_c_std    = 'c99'

cmake = import('cmake')
zlib_vars = cmake.subproject_options()
zlib_vars.set_install(false)
zlib_proj = cmake.subproject('zlib', options : zlib_vars)
zlib_dep = zlib_proj.dependency('zlibstatic')

cnbt_src = [
  'buffer.c',
  'nbt_loading.c',
  'nbt_parsing.c',
  'nbt_treeops.c',
  'nbt_util.c'
]

cnbt_includes = include_directories('.')

cnbt_lib = static_library('cnbt', cnbt_src,
  dependencies        : [ zlib_dep ],
  include_directories : cnbt_includes,
  override_options    : [ 'c_std='+cnbt_c_std ])

cnbt_dep = declare_dependency(
  link_with           : cnbt_lib,
  include_directories : cnbt_includes)