if get_option('with_terminal')

terminal_resources = gnome.compile_resources(
  'gb-terminal-resources',
  'gb-terminal.gresource.xml',
  c_name: 'gb_terminal',
)

terminal_sources = [
  terminal_resources[0],
  terminal_resources[1],
  'gb-terminal.c',
  'gb-terminal.h',
  'gb-terminal-application-addin.c',
  'gb-terminal-application-addin.h',
  'gb-terminal-plugin.c',
  'gb-terminal-private.h',
  'gb-terminal-view.c',
  'gb-terminal-view.h',
  'gb-terminal-view-private.h',
  'gb-terminal-view-actions.c',
  'gb-terminal-view-actions.h',
  'gb-terminal-workbench-addin.c',
  'gb-terminal-workbench-addin.h',
]

terminal_deps = plugin_deps + [
  dependency('vte-2.91 >= 0.40.2'),
]

shared_library('terminal-plugin', terminal_sources,
  dependencies: terminal_deps,
  install: true,
  install_dir: plugindir,
)

install_data('terminal.plugin', install_dir: plugindir)

endif
