libgstyle_headers = [
  'gstyle-animation.h',
  'gstyle-cielab.h',
  'gstyle-color.h',
  'gstyle-color-component.h',
  'gstyle-color-convert.h',
  'gstyle-color-filter.h',
  'gstyle-color-item.h',
  'gstyle-color-panel.h',
  'gstyle-color-panel-private.h',
  'gstyle-color-panel-actions.h',
  'gstyle-color-plane.h',
  'gstyle-color-predefined.h',
  'gstyle-color-scale.h',
  'gstyle-color-widget.h',
  'gstyle-color-widget-actions.h',
  'gstyle-colorlexer.h',
  'gstyle-css-provider.h',
  'gstyle-eyedropper.h',
  'gstyle-hsv.h',
  'gstyle-palette.h',
  'gstyle-palette-widget.h',
  'gstyle-private.h',
  'gstyle-rename-popover.h',
  'gstyle-revealer.h',
  'gstyle-slidein.h',
  'gstyle-types.h',
  'gstyle-utils.h',
  'gstyle-xyz.h',
]

libgstyle_header_dir = path_join(get_option('includedir'),
  'gnome-builder-' + meson.project_version(), 'gstyle')

install_headers(libgstyle_headers,
  install_dir: libgstyle_header_dir,
)

libgstyle_resources = gnome.compile_resources('gstyle-resources',
  'gstyle.gresource.xml',
  c_name: 'gstyle',
)

libgstyle_sources = [
  'gstyle-animation.c',
  'gstyle-cielab.c',
  'gstyle-color.c',
  'gstyle-color-component.c',
  'gstyle-color-convert.c',
  'gstyle-color-filter.c',
  'gstyle-color-item.c',
  'gstyle-color-panel.c',
  'gstyle-color-panel-actions.c',
  'gstyle-color-plane.c',
  'gstyle-color-scale.c',
  'gstyle-color-widget.c',
  'gstyle-color-widget-actions.c',
  'gstyle-colorlexer.c',
  'gstyle-css-provider.c',
  'gstyle-eyedropper.c',
  'gstyle-hsv.c',
  'gstyle-palette.c',
  'gstyle-palette-widget.c',
  'gstyle-rename-popover.c',
  'gstyle-revealer.c',
  'gstyle-slidein.c',
  'gstyle-utils.c',
  'gstyle-xyz.c',
  libgstyle_resources[0],
]

libgstyle_deps = [
  dependency('gtk+-3.0'),
  libsearch_dep,
  libxml_dep,
]

libgstyle = shared_library('gstyle-private', libgstyle_sources,
  dependencies: libgstyle_deps,
  install: true,
  install_dir: pkglibdir,
)

libgstyle_dep = declare_dependency(
  link_with: libgstyle,
  dependencies: libgstyle_deps,
  include_directories: include_directories([
    meson.current_source_dir()
  ])
)

if get_option('with_introspection')

gnome.generate_gir(libgstyle,
  sources: libgstyle_sources + libgstyle_headers,
  nsversion: '1.0',
  namespace: 'Gstyle',
  symbol_prefix: 'gstyle',
  identifier_prefix: 'Gstyle',
  includes: ['Gtk-3.0', 'GtkSource-3.0'],
  install: true,
  install_dir_gir: pkggirdir,
  install_dir_typelib: pkgtypelibdir,
  extra_args: [
    '--c-include=gstyle-private.h',
  ],
)

endif

subdir('tests')
