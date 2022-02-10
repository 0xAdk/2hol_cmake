add_executable(client)

target_link_libraries(client minorGemsClient)

target_compile_features(client PRIVATE cxx_std_17)
target_include_directories(client PRIVATE ${PROJECT_SOURCE_DIR}/src)
target_sources(client PRIVATE
	${PROJECT_SOURCE_DIR}/lib/minorGems/minorGems/game/platforms/SDL/gameSDL.cpp
	${PROJECT_SOURCE_DIR}/src/common/SoundUsage.cpp
	${PROJECT_SOURCE_DIR}/src/common/animationBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/categoryBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/fractalNoise.cpp
	${PROJECT_SOURCE_DIR}/src/common/objectBank.cpp
	${PROJECT_SOURCE_DIR}/src/common/objectMetadata.cpp
	${PROJECT_SOURCE_DIR}/src/common/sayLimit.cpp
	${PROJECT_SOURCE_DIR}/src/common/transitionBank.cpp

	${PROJECT_SOURCE_DIR}/src/client/minitech.cpp
	${PROJECT_SOURCE_DIR}/src/client/game.cpp
	${PROJECT_SOURCE_DIR}/src/client/spriteBank.cpp
	${PROJECT_SOURCE_DIR}/src/client/whiteSprites.cpp
	${PROJECT_SOURCE_DIR}/src/client/message.cpp
	${PROJECT_SOURCE_DIR}/src/client/serialWebRequests.cpp
	${PROJECT_SOURCE_DIR}/src/client/accountHmac.cpp
	${PROJECT_SOURCE_DIR}/src/client/PageComponent.cpp
	${PROJECT_SOURCE_DIR}/src/client/GamePage.cpp
	${PROJECT_SOURCE_DIR}/src/client/LivingLifePage.cpp
	${PROJECT_SOURCE_DIR}/src/client/pathFind.cpp
	${PROJECT_SOURCE_DIR}/src/common/ageControl.cpp
	${PROJECT_SOURCE_DIR}/src/client/ExtendedMessagePage.cpp
	${PROJECT_SOURCE_DIR}/src/client/buttonStyle.cpp
	${PROJECT_SOURCE_DIR}/src/client/Button.cpp
	${PROJECT_SOURCE_DIR}/src/client/TextButton.cpp
	${PROJECT_SOURCE_DIR}/src/client/RebirthChoicePage.cpp
	${PROJECT_SOURCE_DIR}/src/client/TextField.cpp
	${PROJECT_SOURCE_DIR}/src/client/DropdownList.cpp
	${PROJECT_SOURCE_DIR}/src/client/LoadingPage.cpp
	${PROJECT_SOURCE_DIR}/src/common/folderCache.cpp
	${PROJECT_SOURCE_DIR}/src/client/binFolderCache.cpp
	${PROJECT_SOURCE_DIR}/src/client/liveObjectSet.cpp
	${PROJECT_SOURCE_DIR}/src/client/ExistingAccountPage.cpp
	${PROJECT_SOURCE_DIR}/src/client/KeyEquivalentTextButton.cpp
	${PROJECT_SOURCE_DIR}/src/client/ServerActionPage.cpp
	${PROJECT_SOURCE_DIR}/src/client/FinalMessagePage.cpp
	${PROJECT_SOURCE_DIR}/src/client/AutoUpdatePage.cpp
	${PROJECT_SOURCE_DIR}/src/client/soundBank.cpp
	${PROJECT_SOURCE_DIR}/src/client/convolution.cpp
	${PROJECT_SOURCE_DIR}/src/client/fft.cpp
	${PROJECT_SOURCE_DIR}/src/client/ogg.cpp
	${PROJECT_SOURCE_DIR}/src/client/musicPlayer2.cpp
	${PROJECT_SOURCE_DIR}/src/client/groundSprites.cpp
	${PROJECT_SOURCE_DIR}/src/client/SettingsPage.cpp
	${PROJECT_SOURCE_DIR}/src/client/CheckboxButton.cpp
	${PROJECT_SOURCE_DIR}/src/client/ValueSlider.cpp
	${PROJECT_SOURCE_DIR}/src/client/SpriteButton.cpp
	${PROJECT_SOURCE_DIR}/src/client/SpriteToggleButton.cpp
	${PROJECT_SOURCE_DIR}/src/client/liveAnimationTriggers.cpp
	${PROJECT_SOURCE_DIR}/src/client/ReviewPage.cpp
	${PROJECT_SOURCE_DIR}/src/client/TextArea.cpp
	${PROJECT_SOURCE_DIR}/src/client/RadioButtonSet.cpp
	${PROJECT_SOURCE_DIR}/src/client/spellCheck.cpp
	${PROJECT_SOURCE_DIR}/src/client/TwinPage.cpp
	${PROJECT_SOURCE_DIR}/src/client/emotion.cpp
	${PROJECT_SOURCE_DIR}/src/client/Picker.cpp
	${PROJECT_SOURCE_DIR}/src/client/PickableStatics.cpp
	${PROJECT_SOURCE_DIR}/src/client/photos.cpp
	${PROJECT_SOURCE_DIR}/src/client/lifeTokens.cpp
	${PROJECT_SOURCE_DIR}/src/client/PollPage.cpp
	${PROJECT_SOURCE_DIR}/src/client/fitnessScore.cpp
	${PROJECT_SOURCE_DIR}/src/client/GeneticHistoryPage.cpp
)
