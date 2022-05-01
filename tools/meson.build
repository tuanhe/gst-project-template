exe_args = common_args + []

# sources used to compile this program
tool_sources = [
  'gstMyProjct.c',
]

executable('gstMyProjct',
  tool_sources,
  install: true,
  c_args : exe_args,
  include_directories: [configinc],
  dependencies : tool_deps,
)
