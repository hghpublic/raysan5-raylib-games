
find_package(raylib CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

set(targets
    00_drturtle_screens
    01_drturtle_scrolling
    02_drturtle_player
    03_drturtle_enemies
    04_drturtle_gui
    05_drturtle_audio
    06_drturtle_final
    drturtle_final_web
)

foreach(target IN LISTS targets)
add_executable(${target})
target_sources(${target} PRIVATE ${target}.c)
target_link_libraries(${target} PRIVATE raylib)
target_link_libraries(${target} PRIVATE glfw)
target_link_libraries(${target} PRIVATE m)    
endforeach()

# copy resources

set(target 00_drturtle_screens)
add_custom_command(TARGET ${target} POST_BUILD
    COMMAND ${CMAKE_COMMAND} -E copy_directory 
        ${PROJECT_SOURCE_DIR}/src/resources
        $<TARGET_FILE_DIR:${target}>/resources
)
