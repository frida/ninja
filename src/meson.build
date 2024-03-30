sources = [
  'ninja.cc',
  'build.cc',
  'build_log.cc',
  'clean.cc',
  'clparser.cc',
  'debug_flags.cc',
  'depfile_parser.cc',
  'deps_log.cc',
  'disk_interface.cc',
  'dyndep.cc',
  'dyndep_parser.cc',
  'edit_distance.cc',
  'eval_env.cc',
  'graph.cc',
  'graphviz.cc',
  'json.cc',
  'lexer.cc',
  'line_printer.cc',
  'manifest_parser.cc',
  'metrics.cc',
  'missing_deps.cc',
  'parser.cc',
  'state.cc',
  'status.cc',
  'string_piece_util.cc',
  'util.cc',
  'version.cc',
]

if host_machine.system() == 'windows'
  sources += [
    'subprocess-win32.cc',
    'includes_normalize-win32.cc',
    'msvc_helper-win32.cc',
    'msvc_helper_main-win32.cc',
    'getopt.c',
  ]
  if cpp.get_argument_syntax() == 'msvc'
    sources += 'minidump-win32.cc'
  endif
else
  sources += 'subprocess-posix.cc'
endif

executable('ninja', sources,
  implicit_include_directories: false,
  override_options: [
    'cpp_eh=none',
    'cpp_rtti=false',
  ],
  gnu_symbol_visibility: 'hidden',
  install: true,
)
