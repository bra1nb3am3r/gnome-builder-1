libtmpl_headers = [
  'tmpl-error.h',
  'tmpl-expr-types.h',
  'tmpl-expr.h',
  'tmpl-glib.h',
  'tmpl-scope.h',
  'tmpl-symbol.h',
  'tmpl-template-locator.h',
  'tmpl-template.h',
  'tmpl-enums.h',
]

libtmpl_enum_headers = [
  'tmpl-error.h',
  'tmpl-expr-types.h',
]

gnome.mkenums('tmpl-enums',
  sources: libtmpl_enum_headers,
)

install_headers(libtmpl_headers,
  subdir: 'gnome-builder-' + meson.project_version() + '/template-glib',
)

libtmpl_sources = [
  'tmpl-branch-node.c',
  'tmpl-branch-node.h',
  'tmpl-condition-node.c',
  'tmpl-condition-node.h',
  'tmpl-debug.h',
  'tmpl-error.c',
  'tmpl-expr-eval.c',
  'tmpl-expr-node.c',
  'tmpl-expr-node.h',
  'tmpl-expr-parser-private.h',
  'tmpl-expr-private.h',
  'tmpl-expr.c',
  'tmpl-gi-private.h',
  'tmpl-gi.c',
  'tmpl-iter-node.c',
  'tmpl-iter-node.h',
  'tmpl-iterator.c',
  'tmpl-iterator.h',
  'tmpl-lexer.c',
  'tmpl-lexer.h',
  'tmpl-node.c',
  'tmpl-node.h',
  'tmpl-parser.c',
  'tmpl-parser.h',
  'tmpl-scope.c',
  'tmpl-symbol.c',
  'tmpl-template-locator.c',
  'tmpl-template.c',
  'tmpl-text-node.c',
  'tmpl-text-node.h',
  'tmpl-token-input-stream.c',
  'tmpl-token-input-stream.h',
  'tmpl-token.c',
  'tmpl-token.h',
  'tmpl-util-private.h',
  'tmpl-util.c',
]

libtmpl_deps = [
  dependency('gio-2.0'),
  dependency('gobject-introspection-1.0'),
]

flex = find_program('flex')
bison = find_program('bison')

lgen = generator(flex,
  output : '@BASENAME@.c',
  arguments : ['-o', '@OUTPUT@', '@INPUT@']
)

pgen = generator(bison,
  output : ['@BASENAME@.c', '@BASENAME@.h'],
  arguments : ['@INPUT@', '--defines=@OUTPUT1@', '--output=@OUTPUT0@']
)

libtmpl_sources = libtmpl_sources + [
  lgen.process('tmpl-expr-scanner.l'),
  pgen.process('tmpl-expr-parser.y'),
]

libtmpl = shared_library('tmpl', libtmpl_sources,
  dependencies: libtmpl_deps,
  c_args: ['-DTMPL_GLIB_COMPILATION'],
  install: true,
  install_dir: pkglibdir, # Was this the wrong dir?
)
