cmake_minimum_required(VERSION 2.6)

project(Box2Dgdx)

if(UNIX)
	set(BOX2DGDX_INSTALL_BY_DEFAULT ON)
else(UNIX)
	set(BOX2DGDX_INSTALL_BY_DEFAULT OFF)
endif(UNIX)

option(BOX2DGDX_INSTALL "Install Box2Dgdx lib" ${BOX2DGDX_INSTALL_BY_DEFAULT})
option(BOX2DGDX_BUILD_SHARED "Build Box2D shared libraries" ON)
option(BOX2DGDX_BUILD_STATIC "Build Box2D static libraries" OFF)

find_path(BOX2D_INCLUDE_DIR Box2D/Box2D.h)
find_library(BOX2D_LIBRARY Box2D)



add_subdirectory(gdx)

