set(SRC
	stdafx.h
	common.h
	render_queue.h
	draw_queue.h
	mechaspirit.h

	entry.cpp
	game_core.cpp
)

if(MSVC)
    set(LINUXLIBS)
else()
    set(LINUXLIBS dl)
endif()

add_executable(game ${SRC})
target_include_directories(game PRIVATE ${SDL2_INCLUDE_DIRS} ${SDL2TTF_INCLUDE_DIR})
target_link_directories(game PRIVATE ${SDL2TTF_LIBRARY} )
target_link_libraries(game PRIVATE ${SDL2_LIBRARIES} SDL2_ttf glad imgui libgame ${LINUXLIBS})
target_compile_options(game PRIVATE "-mfma")
target_precompile_headers(game PRIVATE "stdafx.h")
ld_builddir(game)
