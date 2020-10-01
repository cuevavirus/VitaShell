add_link_options(
  -nostdlib
  --entry=module_start
)

add_executable(usbdevice
  main.c
)

target_link_libraries(usbdevice
  SceUdcdForDriver_stub
  SceIofilemgrForDriver_stub
  SceSysclibForDriver_stub
  taihenForKernel_stub
)

dolce_create_self(usbdevice.skprx usbdevice CONFIG exports.yml UNSAFE)
