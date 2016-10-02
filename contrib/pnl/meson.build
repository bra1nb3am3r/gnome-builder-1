libpnl_headers = [
  'pnl-animation.h',
  'pnl-dock-bin.h',
  'pnl-dock-bin-edge.h',
  'pnl-dock-item.h',
  'pnl-dock-manager.h',
  'pnl-dock-overlay.h',
  'pnl-dock-paned.h',
  'pnl-dock-revealer.h',
  'pnl-dock-stack.h',
  'pnl-dock-types.h',
  'pnl-dock-widget.h',
  'pnl-dock-window.h',
  'pnl-dock.h',
  'pnl-frame-source.h',
  'pnl-multi-paned.h',
  'pnl-tab-strip.h',
  'pnl-tab.h',
  'pnl-version.h',
  'pnl.h',
]

install_headers(libpnl_headers,
  subdir: 'gnome-builder-' + meson.project_version() + '/pnl',
)

libpnl_resources = gnome.compile_resources('pnl-resources',
  'pnl.gresource.xml',
  c_name: 'pnl',
)

libpnl_sources = [
  'pnl-animation.c',
  'pnl-dock-bin-edge.c',
  'pnl-dock-bin-edge-private.h',
  'pnl-dock-bin.c',
  'pnl-dock-item.c',
  'pnl-dock-manager.c',
  'pnl-dock-overlay-edge-private.h',
  'pnl-dock-overlay-edge.c',
  'pnl-dock-overlay.c',
  'pnl-dock-paned-private.h',
  'pnl-dock-paned.c',
  'pnl-dock-revealer.c',
  'pnl-dock-stack.c',
  'pnl-dock-tab-strip.c',
  'pnl-dock-tab-strip.h',
  'pnl-dock-transient-grab.c',
  'pnl-dock-transient-grab.h',
  'pnl-dock-widget.c',
  'pnl-dock-window.c',
  'pnl-dock.c',
  'pnl-frame-source.c',
  'pnl-multi-paned.c',
  'pnl-tab-strip.c',
  'pnl-tab.c',
  'pnl-util-private.h',
  'pnl-util.c',
  libpnl_resources[0],
  libpnl_resources[1],
]

libpnl_deps = [
  dependency('gtk+-3.0'),
]

libpnl = shared_library('pnl', libpnl_sources,
  dependencies: libpnl_deps,
  c_args: ['-DPNL_COMPILATION'],
  install: true,
  install_dir: get_option('libdir') + '/gnome-builder',
)

if get_option('with_introspection')

gnome.generate_gir(libpnl,
  sources: libpnl_sources + libpnl_headers,
  nsversion: '1.0',
  namespace: 'Pnl',
  symbol_prefix: 'pnl',
  identifier_prefix: 'Pnl',
  includes: ['Gtk-3.0'],
  install: true,
  install_dir_gir: get_option('datadir') + '/gnome-builder/gir-1.0',
  install_dir_typelib: get_option('datadir') + '/gnome-builder/girepository-1.0',
  extra_args: [
    '-DPNL_COMPILATION',
  ],
)

endif
