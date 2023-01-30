project("Main")
cmake_minimum_required(VERSION 3.24)

set(gcc_like_cxx "$<COMPILE_LANG_AND_ID:CXX,ARMClang,AppleClang,Clang,GNU,LCC>")
set(msvc_cxx "$<COMPILE_LANG_AND_ID:CXX,MSVC>")

add_library(tutorial_compiler_flags INTERFACE)

target_compile_features(tutorial_compiler_flags INTERFACE cxx_std_17)

target_compile_options(tutorial_compiler_flags INTERFACE
  "$<${gcc_like_cxx}:$<BUILD_INTERFACE:-Wall;-Wextra;-Wshadow;-Wformat=2;-Wunused>>"
  "$<${msvc_cxx}:$<BUILD_INTERFACE:-W3>>"
)

add_subdirectory(ModuleA)
add_subdirectory(ModuleB)

#add_executable(Main
#  main.cpp
#)

#target_link_libraries(Main PUBLIC 
#  ModuleA
#  tutorial_compiler_flags
#)

# install(TARGETS Main DESTINATION bin)
