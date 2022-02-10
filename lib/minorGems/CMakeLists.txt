add_library(minorGemsCommon STATIC)

find_package(OpenGL REQUIRED)
find_package(SDL REQUIRED)
find_package(Threads REQUIRED)
target_link_libraries(minorGemsCommon PUBLIC
	OpenGL::GL
	OpenGL::GLU
	# don't use SDL::SDL since cmake 1.16 doesn't support it
	${SDL_LIBRARY}
	Threads::Threads
)

message(STATUS "Target system: ${CMAKE_SYSTEM}")
if(CMAKE_SYSTEM MATCHES Linux)
	target_compile_definitions(minorGemsCommon PUBLIC LINUX)

	find_package(X11 REQUIRED)
	target_link_libraries(minorGemsCommon PUBLIC X11::X11)

	set(PLATFORM Linux)
	set(PLATFORM_PATH linux)

	set(TIME_PLATFORM Unix)
	set(TIME_PLATFORM_PATH unix)

	set(DIRECTORY_PLATFORM Unix)
	set(DIRECTORY_PLATFORM_PATH unix)

	set(POLL_PLATFORM Linux)
	set(POLL_PLATFORM_PATH linux)
elseif(CMAKE_SYSTEM MATCHES Windows)
	target_compile_definitions(minorGemsCommon PUBLIC WIN_32 STATICLIB)

	target_link_libraries(minorGemsCommon PUBLIC wsock32 winmm -static)

	set(PLATFORM Win32)
	set(PLATFORM_PATH win32)

	set(TIME_PLATFORM Win32)
	set(TIME_PLATFORM_PATH win32)

	set(DIRECTORY_PLATFORM Win32)
	set(DIRECTORY_PLATFORM_PATH win32)

	set(POLL_PLATFORM Unix)
	set(POLL_PLATFORM_PATH unix)
endif()


target_include_directories(minorGemsCommon PUBLIC .)

target_sources(minorGemsCommon PUBLIC
	./minorGems/io/${PLATFORM_PATH}/TypeIO${PLATFORM}.cpp
	./minorGems/util/stringUtils.cpp
	./minorGems/util/StringBufferOutputStream.cpp
	./minorGems/io/file/${PLATFORM_PATH}/Path${PLATFORM}.cpp
	./minorGems/system/${TIME_PLATFORM_PATH}/Time${TIME_PLATFORM}.cpp
	./minorGems/system/${PLATFORM_PATH}/Thread${PLATFORM}.cpp
	./minorGems/system/${PLATFORM_PATH}/MutexLock${PLATFORM}.cpp
	./minorGems/util/TranslationManager.cpp
	./minorGems/network/${PLATFORM_PATH}/Socket${PLATFORM}.cpp
	./minorGems/network/${PLATFORM_PATH}/HostAddress${PLATFORM}.cpp
	./minorGems/network/${PLATFORM_PATH}/SocketClient${PLATFORM}.cpp
	./minorGems/network/${PLATFORM_PATH}/SocketServer${PLATFORM}.cpp
	./minorGems/network/NetworkFunctionLocks.cpp
	./minorGems/network/LookupThread.cpp
	./minorGems/network/web/WebRequest.cpp
	./minorGems/network/web/URLUtils.cpp
	./minorGems/util/SettingsManager.cpp
	./minorGems/system/FinishedSignalThread.cpp
	./minorGems/crypto/hashes/sha1.cpp
	./minorGems/formats/encodingUtils.cpp
	./minorGems/io/file/${DIRECTORY_PLATFORM_PATH}/Directory${DIRECTORY_PLATFORM}.cpp
	./minorGems/util/log/Log.cpp
	./minorGems/util/log/AppLog.cpp
	./minorGems/util/log/FileLog.cpp
	./minorGems/util/log/PrintLog.cpp
	./minorGems/util/printUtils.cpp
	./minorGems/game/doublePair.cpp
	./minorGems/util/StringTree.cpp
	./minorGems/util/crc32.cpp
)

add_library(minorGemsServer STATIC)
target_link_libraries(minorGemsServer minorGemsCommon)

target_sources(minorGemsServer PUBLIC
	./minorGems/network/${POLL_PLATFORM_PATH}/SocketPoll${POLL_PLATFORM}.cpp
)

add_library(minorGemsClient STATIC)
target_link_libraries(minorGemsClient minorGemsCommon)

target_sources(minorGemsClient PUBLIC
	./minorGems/graphics/openGL/ScreenGL_SDL.cpp
	./minorGems/graphics/openGL/SingleTextureGL.cpp
	./minorGems/util/ByteBufferInputStream.cpp
	./minorGems/system/StopSignalThread.cpp
	./minorGems/system/${PLATFORM_PATH}/BinarySemaphore${PLATFORM}.cpp
	./minorGems/game/platforms/openGL/gameGraphicsGL.cpp
	./minorGems/game/platforms/openGL/SpriteGL.cpp
	./minorGems/game/Font.cpp
	./minorGems/game/drawUtils.cpp
	./minorGems/game/platforms/SDL/DemoCodeChecker.cpp
	./minorGems/sound/formats/aiff.cpp
	./minorGems/sound/audioNoClip.cpp
	./minorGems/sound/filters/SoundSamples.cpp
	./minorGems/sound/filters/ReverbSoundFilter.cpp
	./minorGems/sound/filters/coefficientFilters.cpp
	./minorGems/crypto/keyExchange/curve25519.cpp
	./minorGems/crypto/cryptoRandom.cpp
	./minorGems/game/diffBundle/client/diffBundleClient.cpp
)
