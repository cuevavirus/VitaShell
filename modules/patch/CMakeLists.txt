add_link_options(
  -nostdlib
  --entry=module_start
)

add_executable(patch
  main.c
)

target_link_libraries(patch
  taihenForKernel_stub
)

dolce_create_self(patch.skprx patch CONFIG exports.yml UNSAFE)
