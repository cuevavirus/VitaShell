add_link_options(
  -nostdlib
  --entry=module_start
)

add_executable(kernel
  main.c
)

target_link_libraries(kernel
  SceIofilemgrForDriver_stub
  SceSysclibForDriver_stub
  SceSysmemForDriver_stub
  SceModulemgrForDriver_stub
  SceThreadmgrForDriver_stub
  SceProcessmgrForDriver_stub
  SceNpDrmForDriver_stub
  taihenForKernel_stub
  taihenModuleUtils_stub
)

dolce_create_self(kernel.skprx kernel CONFIG exports.yml UNSAFE)

dolce_create_stubs(vitashell_kernel_stubs kernel exports.yml KERNEL LIB VitaShellKernel2Library_stub)
