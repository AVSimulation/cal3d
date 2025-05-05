cmake_minimum_required(VERSION 3.21)

project(cal3d VERSION 0.12.0)

add_subdirectory(src)

install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/cmake/cal3d-config.cmake DESTINATION "share/cal3d")

include(CMakePackageConfigHelpers)
write_basic_package_version_file(${CMAKE_BINARY_DIR}/cmake/cal3dConfigVersion.cmake
    VERSION ${PROJECT_VERSION}
    COMPATIBILITY SameMajorVersion)
install(FILES ${CMAKE_BINARY_DIR}/cmake/cal3dConfigVersion.cmake
    DESTINATION "share/cal3d")

install(EXPORT cal3d-export
  FILE
  	cal3dTargets.cmake
  NAMESPACE
  	cal3d::
  DESTINATION
    share/cal3d
)
