if get_option('with_docs')

doc_conf = configuration_data()
doc_conf.set('LIBIDE_VERSION', libide_api_version)

subdir('xml')

doc_version_xml = configure_file(
  input: 'version.xml.in',
  output: 'version.xml',
  configuration: doc_conf,
)

# FIXME: Correct prefix for system docs
doc_dir_arg = '--extra-dir=@0@/@1@/gtk-doc/html/'.format('/usr', get_option('datadir'))


gnome.gtkdoc('libide',
  #meson.source_root() + '/libide',
  main_sgml: 'libide-docs.sgml',
  src_dir: meson.source_root() + '/libide',
  dependencies: libide_dep,
  install: true,
  scan_args: [
    '--rebuild-types',
    '--ignore-headers=config.h',
  ],
  fixxref_args: [
    doc_dir_arg + 'glib',
    doc_dir_arg + 'gmodule',
    doc_dir_arg + 'gobject',
    doc_dir_arg + 'gio',
    doc_dir_arg + 'gtk',
    doc_dir_arg + 'gtksourceview-3.0',
  ],
  #content_files: doc_version_xml,
)

endif
