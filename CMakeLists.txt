
cmake_minimum_required(VERSION 2.8)
project(sigrlinn)

set(CMAKE_MODULE_PATH ${CMAKE_MODULE_PATH} "${CMAKE_SOURCE_DIR}/cmake/")

find_package(D3D11 REQUIRED)

file(GLOB src          sigrlinn/*.cc)
file(GLOB hdr          sigrlinn/*.hh)
file(GLOB src_internal sigrlinn/private/*.cc)
file(GLOB hdr_internal sigrlinn/private/*.hh)

file(GLOB demo_src demo/*.cc)
file(GLOB demo_hdr demo/*.hh)

source_group("source"            FILES ${src})
source_group("include"           FILES ${hdr})
source_group("source\\internal"  FILES ${src_internal})
source_group("include\\internal" FILES ${hdr_internal})
source_group("glew"              FILES sigrlinn/GL/glew.c sigrlinn/GL/glew.h sigrlinn/GL/glxew.h sigrlinn/GL/wglew.h)

source_group("demo\\source"  FILES ${demo_src})
source_group("demo\\include" FILES ${demo_hdr})

include_directories(${CMAKE_SOURCE_DIR}/sigrlinn)
add_executable(SigrlinnDemo WIN32
	${demo_src}
	${demo_hdr}
	${src}
	${hdr}
	${src_internal}
	${hdr_internal}

	# GLEW
	sigrlinn/GL/glew.c
	sigrlinn/GL/glew.h
	sigrlinn/GL/glxew.h
	sigrlinn/GL/wglew.h
)