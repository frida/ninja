project('ninja', 'cpp', 'c',
  version: '1.11.1',
  default_options: ['cpp_std=gnu++17,c++17'],
)

cpp = meson.get_compiler('cpp')

if cpp.get_argument_syntax() == 'msvc'
  add_project_arguments(
    '/wd4530', '/wd4100', '/wd4706', '/wd4244', '/wd4512', '/wd4800', '/wd4702',
    '/wd4819', '/wd4127', '/wd4355', '/wd4091', '/wd4267',
    '/DNOMINMAX',
    '/D_CRT_SECURE_NO_WARNINGS',
    '/D_HAS_EXCEPTIONS=0',
    language: 'cpp',
  )
else
  add_project_arguments(
    '-Wno-missing-field-initializers',
    '-Wno-unused-parameter',
    cpp.get_supported_arguments(
      '-Wno-deprecated',
      '-fdiagnostics-color',
    ),
    language: 'cpp',
  )
endif

if host_machine.system() == 'windows' and cpp.get_argument_syntax() != 'msvc'
  add_project_arguments('-D__USE_MINGW_ANSI_STDIO=1', language: 'cpp')
endif

if cpp.has_function('ppoll', prefix: '#include <poll.h>')
  add_project_arguments('-DUSE_PPOLL', language: 'cpp')
endif

subdir('src')
