cmake_minimum_required(VERSION 3.18)

include_directories(${RAKNET_INTERNAL_INCLUDE_DIRS}) 

add_library(RakNet SHARED)
target_sources(RakNet PRIVATE ${RAKNET_CPP_SRCS} ${ALL_HEADER_SRCS})

IF(WIN32 AND NOT UNIX)
	SET(CMAKE_CXX_FLAGS "/D WIN32 /D _RAKNET_DLL /D _CRT_NONSTDC_NO_DEPRECATE /D _CRT_SECURE_NO_DEPRECATE /GS- /GR- ")
ENDIF(WIN32 AND NOT UNIX)

IF(WIN32 AND NOT UNIX)
	target_link_libraries(RakNet ${RAKNET_LIBRARY_LIBS})
ELSE()
	target_link_libraries(RakNet ${RAKNET_LIBRARY_LIBS})
	#INSTALL(TARGETS RakNet DESTINATION ${RakNet_SOURCE_DIR}/Lib/Shared)
ENDIF(WIN32 AND NOT UNIX)
