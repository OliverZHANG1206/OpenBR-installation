if(UNIX)
  find_package(Threads REQUIRED)
endif()

add_executable(br br.cpp ${BR_RESOURCES})
target_link_libraries(br openbr ${CMAKE_THREAD_LIBS_INIT})
target_link_libraries(br Qt5::Core)

install(TARGETS br RUNTIME DESTINATION bin)
add_test(NAME br_initialize WORKING_DIRECTORY ${PROJECT_SOURCE_DIR} COMMAND br)

