project('gnome-builder', 'c',
  license: 'GPL3+',
  version: '3.22.0',
  meson_version: '>=0.36.0',
  # https://github.com/mesonbuild/meson/pull/834
  default_options: ['b_lundef=false'],
)

version_split = meson.project_version().split('.')
MAJOR_VERSION = version_split[0]
MINOR_VERSION = version_split[1]
MICRO_VERSION = version_split[2]

conf = configuration_data()
conf.set_quoted('PACKAGE_NAME', 'gnome-builder')
conf.set_quoted('PACKAGE_VERSION', meson.project_version())
conf.set_quoted('PACKAGE_STRING', 'gnome-builder-' + meson.project_version())
conf.set_quoted('PACKAGE_DATADIR', get_option('datadir'))
conf.set_quoted('PACKAGE_LIBDIR', get_option('datadir'))
conf.set_quoted('PACKAGE_LOCALE_DIR', path_join(get_option('datadir'), 'locale'))
conf.set_quoted('PACKAGE_LIBEXECDIR', get_option('libexecdir'))

conf.set('GETTEXT_PACKAGE', 'PACKAGE_NAME')
conf.set('LOCALEDIR', 'PACKAGE_LOCALE_DIR')

conf.set10('ENABLE_NLS', true) # Always enabled

# We should probably avoid using these
conf.set_quoted('SRCDIR', meson.source_root())
conf.set_quoted('BUILDDIR', meson.build_root())

add_global_arguments([
  '-DHAVE_CONFIG_H',
  '-I' + meson.build_root(), # config.h
  '-D_GNU_SOURCE',
], language: 'c')

cc = meson.get_compiler('c')
global_c_args = []
test_c_args = [
  '-Wall',
  '-Wcast-align',
  '-Wdeclaration-after-statement',
  '-Werror=format-security',
  '-Werror=format=2',
  '-Wextra',
  '-Wformat-nonliteral',
  '-Wformat-security',
  '-Wmissing-include-dirs',
  '-Wnested-externs',
  '-Wno-missing-field-initializers',
  '-Wno-sign-compare',
  '-Wno-strict-aliasing',
  '-Wno-uninitialized',
  '-Wno-unused-parameter',
  '-Wpointer-arith',
  '-Wredundant-decls',
  '-Wshadow',
  '-Wswitch-default',
  '-Wswitch-enum',
  '-fstack-protector-strong',
]
foreach arg: test_c_args
  if cc.has_argument(arg)
    global_c_args += arg
  endif
endforeach
add_global_arguments(
  global_c_args,
  language: 'c'
)

global_link_args = []
test_link_args = [
  '-Wl,-z,relro',
  '-Wl,-z,now',
]
foreach arg: test_link_args
  if cc.has_argument(arg)
    global_link_args += arg
  endif
endforeach
add_global_link_arguments(
  global_link_args,
  language: 'c'
)

if cc.has_function('sched_getcpu')
  conf.set('HAVE_SCHED_GETCPU', true)
endif

configure_file(
  input: 'config.h.meson',
  output: 'config.h',
  configuration: conf
)

pkglibdir = path_join(get_option('libdir'), 'gnome-builder')
pkggirdir = path_join(get_option('datadir'),' gnome-builder', 'gir-1.0')
pkgtypelibdir = path_join(get_option('datadir'), 'gnome-builder', 'girepository-1.0')
gnome = import('gnome')

subdir('data')
subdir('data/fonts')
subdir('data/gsettings')
subdir('data/icons')
subdir('data/style-schemes')
subdir('contrib/egg')
subdir('contrib/gd')
subdir('contrib/libeditorconfig')
subdir('contrib/nautilus')
subdir('contrib/pnl')
subdir('contrib/rg')
subdir('contrib/search')
subdir('contrib/tmpl')
subdir('contrib/xml')
subdir('contrib/gstyle') # Depends on libsearch/libxml
subdir('libide')
subdir('doc/reference/libide')
subdir('plugins')
subdir('po')
subdir('tests')

executable('gnome-builder', 'src/main.c',
  gui_app: true,
  install: true,
  c_args: '-fPIE',
  link_args: '-pie',
  dependencies: libide_deps + [libide_dep],
)
