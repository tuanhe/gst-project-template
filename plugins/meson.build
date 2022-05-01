lib_args = common_args + []

# sources used to compile this plug-in
plugin_sources = [
  'gstMyProjectplugin.c',
  'gstMyProject.c',
  'gstMyProject.h'
]

shlib = shared_library('gstMyProject',
  plugin_sources,
  c_args : lib_args,
  include_directories: [configinc],
  dependencies : plugin_deps,
  gnu_symbol_visibility : 'hidden',
  install : true,
  install_dir : plugins_install_dir,
)

# Make this library usable as a Meson subproject.
gst_MyProject_dep = declare_dependency(
  include_directories: include_directories('.'),
  link_with : shlib)

pkg_mod = import('pkgconfig')
pkg_mod.generate(
  name : 'gst-MyProject',
  filebase : 'gst-MyProject',
  description : 'Meson sample project.',
  subdirs : 'src',
  libraries : shlib,
  version : '"@0@"'.format(meson.project_version()),
)
