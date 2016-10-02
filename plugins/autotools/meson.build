
autotools_sources = [
  'autotools-plugin.c',
  'ide-autotools-builder.c',
  'ide-autotools-builder.h',
  'ide-autotools-build-system.c',
  'ide-autotools-build-system.h',
  'ide-autotools-build-target.c',
  'ide-autotools-build-target.h',
  'ide-autotools-build-task.c',
  'ide-autotools-build-task.h',
  'ide-autotools-project-miner.c',
  'ide-autotools-project-miner.h',
  'ide-makecache.c',
  'ide-makecache.h',
  'ide-makecache-target.c',
  'ide-makecache-target.h',
]

autotools_deps = [
  dependency('gio-2.0'),
  dependency('libpeas-1.0'),
  dependency('gtksourceview-3.0'),
]

autotools_includes = [
  meson.source_root() + '/contrib/egg',
  meson.source_root() + '/contrib/pnl',
  meson.source_root() + '/libide',
]

shared_library('autotools-plugin', autotools_sources,
  dependencies: autotools_deps,
  include_directories: include_directories(autotools_includes),
  link_with: [libegg, libpnl],
  c_args: ['-DGNU_MAKE_NAME="make"'],
  install: true,
  install_dir: plugindir,
)

install_data('autotools.plugin', install_dir: plugindir)
