add_executable(server)

target_link_libraries(server minorGemsServer)

target_compile_features(server PRIVATE cxx_std_17)
target_compile_definitions(server PRIVATE LINUX)
target_include_directories(server PRIVATE ${PROJECT_SOURCE_DIR}/src)
target_sources(server PRIVATE
	${PROJECT_SOURCE_DIR}/src/common/SoundUsage.cpp
	${PROJECT_SOURCE_DIR}/src/common/ageControl.cpp
	${PROJECT_SOURCE_DIR}/src/common/animationBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/categoryBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/folderCache.cpp
	${PROJECT_SOURCE_DIR}/src/common/fractalNoise.cpp
	${PROJECT_SOURCE_DIR}/src/common/objectBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/objectMetadata.cpp
	${PROJECT_SOURCE_DIR}/src/common/sayLimit.cpp
	${PROJECT_SOURCE_DIR}/src/common/transitionBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/GridPos.cpp

	${PROJECT_SOURCE_DIR}/src/server/server.cpp
	${PROJECT_SOURCE_DIR}/src/server/map.cpp
	${PROJECT_SOURCE_DIR}/src/server/kissdb.cpp
	${PROJECT_SOURCE_DIR}/src/server/lineardb3.cpp
	${PROJECT_SOURCE_DIR}/src/server/lifeLog.cpp
	${PROJECT_SOURCE_DIR}/src/server/foodLog.cpp
	${PROJECT_SOURCE_DIR}/src/server/backup.cpp
	${PROJECT_SOURCE_DIR}/src/server/triggers.cpp
	${PROJECT_SOURCE_DIR}/src/server/dbCommon.cpp
	${PROJECT_SOURCE_DIR}/src/server/playerStats.cpp
	${PROJECT_SOURCE_DIR}/src/server/lineageLog.cpp
	${PROJECT_SOURCE_DIR}/src/server/failureLog.cpp
	${PROJECT_SOURCE_DIR}/src/server/names.cpp
	${PROJECT_SOURCE_DIR}/src/server/monument.cpp
	${PROJECT_SOURCE_DIR}/src/server/lineageLimit.cpp
	${PROJECT_SOURCE_DIR}/src/server/curses.cpp
	${PROJECT_SOURCE_DIR}/src/server/curseLog.cpp
	${PROJECT_SOURCE_DIR}/src/server/spiral.cpp
	${PROJECT_SOURCE_DIR}/src/server/objectSurvey.cpp
	${PROJECT_SOURCE_DIR}/src/server/language.cpp
	${PROJECT_SOURCE_DIR}/src/server/familySkipList.cpp
	${PROJECT_SOURCE_DIR}/src/server/lifeTokens.cpp
	${PROJECT_SOURCE_DIR}/src/server/fitnessScore.cpp
	${PROJECT_SOURCE_DIR}/src/server/CoordinateTimeTracking.cpp
	${PROJECT_SOURCE_DIR}/src/server/arcReport.cpp
	${PROJECT_SOURCE_DIR}/src/server/curseDB.cpp
	${PROJECT_SOURCE_DIR}/src/server/cravings.cpp
)
