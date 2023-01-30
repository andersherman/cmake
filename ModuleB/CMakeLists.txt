project("ModuleB")

add_library(ModuleB 
  ModuleB.cpp
)

target_link_libraries(ModuleB
  tutorial_compiler_flags
)

target_include_directories(ModuleB
  INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/include 
)

set(installable_libs ModuleB tutorial_compiler_flags)

install(TARGETS ${installable_libs} DESTINATION lib)
install(FILES include/ModuleB/ModuleB.hpp DESTINATION include/ModuleB)
