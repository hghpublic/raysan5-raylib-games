
find_package(raylib CONFIG REQUIRED)
find_package(glfw3 CONFIG REQUIRED)

set(targets
    arkanoid
    asteroids
    asteroids_survival
    floppy
    gold_fever
    gorilas
    missile_commander
    pang
    platformer
    snake
    space_invaders
    tetris
)

foreach(target IN LISTS targets)
add_executable(${target})
target_sources(${target} PRIVATE ${target}.c)
target_link_libraries(${target} PRIVATE raylib)
target_link_libraries(${target} PRIVATE glfw)
target_link_libraries(${target} PRIVATE m)    
endforeach()

