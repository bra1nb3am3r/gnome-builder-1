if get_option('with_autotools')

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

shared_library('autotools-plugin', autotools_sources,
  dependencies: plugin_deps,
  c_args: ['-DGNU_MAKE_NAME="make"'], # FIXME: Detect make bin
  install: true,
  install_dir: plugindir,
)

install_data('autotools.plugin', install_dir: plugindir)

endif
