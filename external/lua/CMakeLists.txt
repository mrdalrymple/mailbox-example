cmake_minimum_required(VERSION 3.5)

project (lua C)

file (
  GLOB SRCS
  "*.c"
)

set (
	CFLAGS
	-g
	-pedantic
	-Wextra
	-Wshadow
	-Wsign-compare
	-Wundef
	-Wwrite-strings
	-Wredundant-decls
	-Wdisabled-optimization
	-Wdeclaration-after-statement
	-Wmissing-prototypes
	-Wnested-externs
	-Wstrict-prototypes
	-Wc++-compat
	-Wold-style-definition

	-std=c99
	-DLUA_COMPAT_5_2
)

if (LINUX)
set (
	CFLAGS
	${CFLAGS}
	-DLUA_USE_LINUX
	)
endif (LINUX)


set (
	LDFLAGS
	${CFLAGS}
)

set( CMAKE_CXX_FLAGS  "${CMAKE_C_FLAGS} ${CFLAGS}" )
set( CMAKE_EXE_LINKER_FLAGS  "${CMAKE_EXE_LINKER_FLAGS} ${LDFLAGS}" )

add_library(lua STATIC ${SRCS})
