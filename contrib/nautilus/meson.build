libnautilus_sources = [
  'nautilus-floating-bar.c',
]

libnautilus_deps = [
  dependency('gio-2.0'),
  dependency('gtk+-3.0'),
]

libnautilus = static_library('nautilus', libnautilus_sources,
  dependencies: libnautilus_deps,
  pic: true,
)

libnautilus_dep = declare_dependency(
  link_with: libnautilus,
  include_directories: include_directories([
    meson.current_source_dir(),
  ]),
)
