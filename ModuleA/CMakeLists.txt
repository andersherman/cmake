project("ModuleA")

add_library(ModuleA 
  ModuleA.cpp
)

target_link_libraries(ModuleA
  tutorial_compiler_flags
)


target_include_directories(ModuleA
  INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/include 
)

set(installable_libs ModuleA tutorial_compiler_flags)

install(TARGETS ${installable_libs} DESTINATION lib)
install(FILES include/ModuleA/ModuleA.hpp DESTINATION include/ModuleA)
