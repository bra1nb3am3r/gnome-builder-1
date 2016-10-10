project('gnome-builder', 'c',
  license: 'GPL3+',
  version: '3.22.0',
  meson_version: '>=0.36.0',
  # https://github.com/mesonbuild/meson/pull/834
  default_options: ['b_lundef=false'],
)

MAJOR_VERSION = '3'
MINOR_VERSION = '20'
MICRO_VERSION = '0'

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

# We should probably avoid using these
conf.set_quoted('SRCDIR', meson.source_root())
conf.set_quoted('BUILDDIR', meson.build_root())

add_global_arguments([
  '-DHAVE_CONFIG_H',
  '-I' + meson.build_root(), # config.h
  '-D_GNU_SOURCE',
  '-fPIC', '-fPIE', # Doesn't work?
], language: 'c')

add_global_link_arguments([
  '-fpie', '-Wl,-z,relro', '-Wl,-z,now',
], language: 'c')

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
subdir('contrib/gstyle')
subdir('contrib/libeditorconfig')
subdir('contrib/nautilus')
subdir('contrib/pnl')
subdir('contrib/rg')
subdir('contrib/search')
subdir('contrib/tmpl')
subdir('contrib/xml')
subdir('libide')
subdir('doc/reference/libide')
subdir('plugins')
subdir('po')

executable('gnome-builder', 'src/main.c',
  gui_app: true,
  install: true,
  dependencies: libide_deps + [libide_dep],
)
