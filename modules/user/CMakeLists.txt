add_link_options(
  -nostdlib
  --entry=module_start
)

include_directories(
  ../kernel
)

add_executable(user
  main.c
)

target_link_libraries(user
  VitaShellKernel2Library_stub
  SceLibKernel_stub
  SceIofilemgr_stub
)

dolce_create_self(user.suprx user CONFIG exports.yml UNSAFE)

dolce_create_stubs(vitashell_user_stubs user exports.yml LIB VitaShellUserLibrary_stub_weak)
