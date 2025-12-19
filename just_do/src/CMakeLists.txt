
find_package(raylib CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

set(target ${PROJECT_NAME})
add_executable(${target})
target_sources(${target} PRIVATE
    just_do.c
    screen_level00.c
    screen_level01.c
    screen_level02.c
    screen_level03.c
    screen_level04.c
    screen_level05.c
    screen_level06.c
    screen_level07.c
    screen_level08.c
    screen_level09.c
    screen_level10.c
    screen_logo.c
)
target_link_libraries(${target} PRIVATE raylib)
target_link_libraries(${target} PRIVATE glfw)
target_link_libraries(${target} PRIVATE m)    

# copy resources

add_custom_command(TARGET ${target} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory 
        ${CMAKE_CURRENT_SOURCE_DIR}/resources
        $<TARGET_FILE_DIR:${target}>/resources
)
