include_directories(
	/home/neon/Desktop/ffmpeg/libavformat
	/home/neon/Desktop/ffmpeg/
	/home/neon
        /home/neon/pspdev/psp/include
	"${PROJECT_SOURCE_DIR}/lib/xtool"
	"${PROJECT_SOURCE_DIR}/lib/xgraph"
	"${PROJECT_SOURCE_DIR}/lib/xsound"
)

SET(vangers_SRCS
	3d/3d_math.cpp
	3d/3dgraph.cpp
	3d/3dobject.cpp
	3d/dynamics.cpp
	3d/optimize.cpp
	actint/aci_scr.cpp
	actint/actint.cpp
	actint/actintml.cpp
	actint/ascr_fnc.cpp
	actint/ascript.cpp
	actint/chtree.cpp
	actint/sscript.cpp
	backg.cpp
	dast/poly3d.cpp
	iscreen/controls.cpp
	iscreen/hfont.cpp
	iscreen/i_chat.cpp
	iscreen/iextern.cpp
	iscreen/ikeys.cpp
	iscreen/imap_fnc.cpp
	iscreen/iml.cpp
	iscreen/iscr_fnc.cpp
	iscreen/iscreen.cpp
	iscreen/iscript.cpp
	iscreen/ivmap.cpp
	iscreen/script.cpp
	iscreen/smooth.cpp
	network.cpp
	palette.cpp
	particle/bmp2scr.cpp
	particle/deform.cpp
	particle/df.cpp
	particle/light.cpp
	particle/particle.cpp
	particle/partmap.cpp
	particle/pmaptype.cpp
	rle.cpp
	road.cpp
	sound/music.cpp
	sound/sound.cpp
	#sqint/sqibody.cpp #FOR surmap
	#sqint/sqicore.cpp #FOR surmap
	terra/compress.cpp
	terra/huff1.cpp
	terra/land.cpp
	terra/perpslop.cpp
	terra/siderend.cpp #ASM
	terra/slopskip.cpp
	terra/splay.cpp
	terra/vmap.cpp #ASM
	units/effect.cpp
	units/hobj.cpp
	units/items.cpp
	units/mechos.cpp
	units/moveland.cpp
	units/sensor.cpp
	units/track.cpp
	uvs/diagen.cpp
	uvs/screen.cpp
	uvs/univang.cpp
	xjoystick.cpp
	xsocket.cpp
	zmod_client.cpp
	${WINDOWS_RES}
        actint/layout.h)


	ADD_EXECUTABLE(vangers ${vangers_SRCS})

	IF(WIN32)
		SET(WIN_LIB
			wsock32
			#-mwindows
			#-Wl,-subsystem,windows
		)
	ENDIF(WIN32)
        
	TARGET_LINK_LIBRARIES(vangers
		SDL2main
    ${CMAKE_SOURCE_DIR}/clunk/libclunk.a
		${OGG_LIBRARY}
		${VORBIS_LIBRARY}
		${VORBISFILE_LIBRARY}
		${FFMPEG_LIBRARIES}
		${ZLIB_LIBRARIES}
		${OPENGL_LIBRARIES}
		xtool
		xgraph
		xsound
		${PSPDEV}/psp/lib/libSDL2.a
		${PSPDEV}/psp/lib/libGL.a
		${PSPDEV}/psp/lib/libGLU.a
		${PSPDEV}/psp/lib/libglut.a
    #/usr/lib/x86_64-linux-gnu/libavcodec.a
		psphprm
		pspgu
		pspvfpu
		pspdebug
		pspdisplay
		pspge
		pspctrl
		pspaudio
		pspaudiolib
		psputility
		pspvram
		#-lpspvram
		#-lpsphprm
		#-lpspvfpu	
		#-lpsppower 
		#-lpspdebug 
		#-lpspgu 
		#-lpspctrl 
		#-lpspge 
		#-lpspdisplay 
		#-lpspsdk 
		#-lpsprtc 
		#-lpspaudio 
		#-lc 
		#-lpsputility 
		#-lpspnet 
		#-lpspnet_inet 
		#-lpspnet_apctl 
		#-lpspnet_resolver 
		#-lpspuser 
		#-lz 
	)

create_pbp_file(
    TARGET ${PROJECT_NAME}
    ICON_PATH NULL
    BACKGROUND_PATH NULL
    PREVIEW_PATH NULL
    TITLE ${PROJECT_NAME}
)
