cmake_minimum_required(VERSION 3.0)
project(example_effect)

list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_LIST_DIR}/cmake/Modules)

include(CPM)

CPMAddPackage(
	NAME              blink
	GITHUB_REPOSITORY colugomusic/blink
	GIT_TAG           master
	DOWNLOAD_ONLY     YES
)

add_subdirectory(${blink_SOURCE_DIR}/lib/plugin blink_plugin)

list(APPEND SRC
	./src/dsp.hpp
	./src/model.h
	./src/plugin.cpp
)

list(APPEND RES
	./res/icon.png
)

blink_plugin_add_effect("example_effect" "${SRC}" "${RES}")