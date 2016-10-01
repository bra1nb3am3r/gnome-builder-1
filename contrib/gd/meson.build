libgd_resources = gnome.compile_resources('gd-resources',
  'gd-tagged-entry.gresource.xml',
  source_dir: meson.current_source_dir(),
  c_name: 'gd',
)

libgd_sources = [
  'gd-tagged-entry.c',
  libgd_resources,
]

libgd_deps = [
  dependency('gio-2.0'),
  dependency('gtk+-3.0'),
]

libgd = static_library('gd', libgd_sources,
  dependencies: libgd_deps,
  c_args: ['-fPIC'],
)
