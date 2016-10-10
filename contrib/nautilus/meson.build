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
