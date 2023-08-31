include_directories(
	"${PROJECT_SOURCE_DIR}/lib/xtool"
	"${PROJECT_SOURCE_DIR}/lib/xgraph"
	/home/neon/Desktop/ffmpeg/libavformat
	/home/neon/Desktop/ffmpeg/libavcodec
	/home/neon
	/home/neon/Desktop/ffmpeg/
)

SET(xsound_SRCS
	xsound.cpp
	ogg_stream.cpp
)

if (ANDROID)
	ADD_LIBRARY(xsound OBJECT ${xsound_SRCS})
else()
	ADD_LIBRARY(xsound STATIC ${xsound_SRCS})
	TARGET_LINK_LIBRARIES(xsound
		/usr/lib
		${FFMPEG_LIBRARIES}
		${OGG_LIBRARY}
		${VORBIS_LIBRARY}
		${VORBISFILE_LIBRARY}
	)
endif()
