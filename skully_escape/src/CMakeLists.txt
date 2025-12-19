
find_package(raylib CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

set(target ${PROJECT_NAME})
add_executable(${target})
target_sources(${target} PRIVATE
    skully_escape.c
    monster.c
    player.c
    screen_aisle01.c
    screen_aisle02.c
    screen_armory.c
    screen_attic.c
    screen_bathroom.c
    screen_ending.c
    screen_kitchen.c
    screen_livingroom.c
    screen_logo.c
    screen_title.c
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
