libxml_sources = [
  'xml-reader.c',
]

libxml_deps = [
  dependency('gio-2.0'),
  dependency('libxml-2.0'),
]

libxml = static_library('xml', libxml_sources,
  dependencies: libxml_deps,
  pic: true,
)

libxml_dep = declare_dependency(
  link_with: libxml,
  dependencies: dependency('libxml-2.0'),
  include_directories: include_directories([
    meson.current_source_dir(),
  ]),
)
