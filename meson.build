project(
  'utf8cpp',
  'cpp',
  version: '4.0.8',
  meson_version: '>=0.56',
  default_options: ['cpp_std=c++14'],
)

utf8cpp_dep = declare_dependency(include_directories: include_directories('source'))

utf8cpp_lib = library(
  'utf8cpp',
  include_directories: include_directories('source'),
  install_dir: get_option('libdir'),
  build_by_default: false,
)

install_headers('source/utf8.h', subdir: 'utf8cpp')
install_subdir('source/utf8', install_dir: 'include/utf8cpp')

pkgconfig = import('pkgconfig')
pkgconfig.generate(
  name: 'utf8cpp',
  description: 'C++ portable library for working with utf-8 encoding',
  version: meson.project_version(),
  libraries: utf8cpp_lib,
  install_dir: join_paths(get_option('datadir'), 'utf8cpp', 'pkgconfig'),
)

if get_option('enable_tests')
  subdir('tests')
endif
