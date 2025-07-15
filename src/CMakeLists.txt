add_subdirectory(sample_library)
add_subdirectory(ftxui_sample)

if(cpp_lab_BUILD_FIND_SUBMATRIX)
  message(STATUS "Building find_submatrix executable")
  add_subdirectory(find_submatrix)
else()
  message(STATUS "Skipping find_submatrix executable build")
endif()
