libsearch_sources = [
  'fuzzy.c',
  'trie.c',
]

libsearch_deps = [
  dependency('gobject-2.0'),
]

libsearch = static_library('search', libsearch_sources,
  dependencies: libsearch_deps,
  pic: true,
)
