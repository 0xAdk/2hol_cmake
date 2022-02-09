# For linux only
set(PLATFORM Linux)
set(PLATFORM_PATH linux)

set(TIME_PLATFORM Unix)
set(TIME_PLATFORM_PATH unix)

set(DIRECTORY_PLATFORM Unix)
set(DIRECTORY_PLATFORM_PATH unix)

add_library(minorGemsCommon STATIC)

# TODO: replace GLU in link_libraries with GLUT
#       (this will require replacing deprecated functions)
# find_package(GLUT REQUIRED)
find_package(OpenGL REQUIRED)
find_package(SDL REQUIRED)
find_package(X11 REQUIRED)
find_package(Threads REQUIRED)
target_link_libraries(minorGemsCommon GLU OpenGL::OpenGL SDL::SDL X11::X11 Threads::Threads)

target_compile_definitions(minorGemsCommon PUBLIC LINUX)
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
	./minorGems/network/${PLATFORM_PATH}/SocketPoll${PLATFORM}.cpp
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
