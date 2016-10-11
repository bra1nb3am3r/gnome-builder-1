if get_option('with_gettext')

gettext_sources = [
  'ide-gettext-diagnostic-provider.c',
  'ide-gettext-diagnostic-provider.h',
  'gettext-plugin.c',
]

shared_library('gettext-plugin', gettext_sources,
  dependencies: plugin_deps,
  install: true,
  install_dir: plugindir,
)

install_data('gettext.plugin', install_dir: plugindir)

endif
