cmake_minimum_required(VERSION 3.20)

project(qtm-calc LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Boost)
if(Boost_FOUND)

  if(MSVC)
    set(WINDOWS_EXPORT_ALL_SYMBOLS TRUE)
  endif()
  add_library(libqtmcalc SHARED)

  set_target_properties(libqtmcalc PROPERTIES PREFIX "")

  target_sources(libqtmcalc PRIVATE
    ${CMAKE_CURRENT_SOURCE_DIR}/src/core.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/src/data.cpp
  )

  target_include_directories(libqtmcalc PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include ${Boost_INCLUDE_DIRS})
  target_link_libraries(libqtmcalc PRIVATE ${Boost_LIBRARIES})

endif()
