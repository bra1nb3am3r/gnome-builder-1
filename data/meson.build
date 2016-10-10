msgfmt = find_program('msgfmt')
podir = path_join(meson.source_root(), 'po')

# Desktop launcher and description file.
custom_target(
  'desktop-file',
  input: 'org.gnome.Builder.desktop.in.in',
  output: 'org.gnome.Builder.desktop',
  install: true,
  install_dir: path_join(get_option('datadir'), 'applications'),
  command: [msgfmt, '--desktop', '--template', '@INPUT@',
    '-d', podir, '-o', '@OUTPUT@'],
)

# Appdata file.
custom_target(
  'appdata-file',
  input: 'org.gnome.Builder.appdata.xml.in',
  output: 'org.gnome.Builder.appdata.xml',
  install: true,
  install_dir: path_join(get_option('datadir'), 'appdata'),
  command: [msgfmt, '--xml', '--template', '@INPUT@',
    '-d', podir, '-o', '@OUTPUT@'],
)

# D-Bus service file.
dbusconf = configuration_data()
dbusconf.set('bindir', path_join(get_option('prefix'), get_option('bindir')))
configure_file(
	input: 'org.gnome.Builder.service.in',
	output: 'org.gnome.Builder.service',
	configuration: dbusconf,
	install: true,
	install_dir: path_join(get_option('datadir'), 'dbus-1', 'services'),
)

# pkg-config files.
pkgpkgconfdir = path_join(get_option('libdir'), 'gnome-builder', 'pkgconfig')

pkgconf = configuration_data()
pkgconf.set('prefix', get_option('prefix'))
pkgconf.set('libdir', path_join('${exec_prefix}', get_option('libdir')))
pkgconf.set('VERSION', meson.project_version())

# TODO: Use the pkgconfig module to generate these

configure_file(
	input: 'libide-1.0.pc.in',
	output: 'libide-1.0.pc',
	configuration: pkgconf,
	install: true,
	install_dir: pkgpkgconfdir,
)

configure_file(
	input: 'template-glib-1.0.pc.in',
	output: 'template-glib-1.0.pc',
	configuration: pkgconf,
	install: true,
	install_dir: pkgpkgconfdir,
)

