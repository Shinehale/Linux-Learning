cmake_minimum_required( VERSION 2.8 )

project( Demo4 )

configure_file(
	"${ PROJECT_SOURCE_DIR } /config.h.in"
	"${ PROJECT_SOURCE_DIR } /config.h"
)

option ( USE_MYMATH 
	"Use provided math implementation" ON )

if ( USE_MYMATH ) 
	include_directories ( "${PROJECT_SOURCE_DIR}/math" )
	add_subdirectory( math )
	set ( EXTRA_LIBS ${EXTRA_LIBS} MathFunctions )
endif ( USE_MYMATH )


aux_source_directory( . DIR_SRCS ) 

add_executable( Demo ${DIR_SRCS} )
target_link_libraries( Demo ${EXTRA_LIBS} )
