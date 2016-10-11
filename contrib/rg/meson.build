librg_sources = [
  'realtime-graphs.h',
  'rg-column.c',
  'rg-column.h',
  'rg-column-private.h',
  'rg-cpu-graph.c',
  'rg-cpu-graph.h',
  'rg-cpu-table.c',
  'rg-cpu-table.h',
  'rg-graph.c',
  'rg-graph.h',
  'rg-line-renderer.c',
  'rg-line-renderer.h',
  'rg-renderer.c',
  'rg-renderer.h',
  'rg-ring.c',
  'rg-ring.h',
  'rg-table.c',
  'rg-table.h',
]

librg_deps = [
  dependency('gio-2.0'),
  dependency('gtk+-3.0'),
  libegg_dep,
]

librg = static_library('rg', librg_sources,
  dependencies: librg_deps,
  pic: true,
)

librg_dep = declare_dependency(
  link_with: librg,
  include_directories: include_directories([
    meson.current_source_dir(),
  ]),
)
