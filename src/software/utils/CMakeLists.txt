## AliceVision
## Utilities software

# Uncertainty
if(ALICEVISION_HAVE_UNCERTAINTYTE)
    add_executable(aliceVision_utils_computeUncertainty main_computeUncertainty.cpp)
    
    target_link_libraries(aliceVision_utils_computeUncertainty
      aliceVision_sfm
      ${Boost_LIBRARIES}
      ${UNCERTAINTYTE_LIBRARY}
      ${CUDA_LIBRARIES}
      ${CUDA_CUBLAS_LIBRARIES}
      ${CUDA_cusparse_LIBRARY}
    )
    target_include_directories(aliceVision_utils_computeUncertainty
      PUBLIC
        ${UNCERTAINTYTE_INCLUDE_DIR}
    )
    
    message(warning "UNCERTAINTYTE_LIBRARY: ${UNCERTAINTYTE_LIBRARY}")
    message(warning "CUDA_LIBRARIES: ${CUDA_LIBRARIES}")
    message(warning "CUDA_CUBLAS_LIBRARIES: ${CUDA_CUBLAS_LIBRARIES}")
    message(warning "CUDA_cusparse_LIBRARY: ${CUDA_cusparse_LIBRARY}")
    
    set_property(TARGET aliceVision_utils_computeUncertainty
      PROPERTY FOLDER Software/Utils
    )
    
    install(TARGETS aliceVision_utils_computeUncertainty
      DESTINATION bin/
    )
endif()

# Voctree creation

add_executable(aliceVision_utils_voctreeCreation main_voctreeCreation.cpp)

target_link_libraries(aliceVision_utils_voctreeCreation
	aliceVision_voctree
	aliceVision_feature
	${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_voctreeCreation
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_voctreeCreation
	DESTINATION bin/
)

# Voctree query utility

add_executable(aliceVision_utils_voctreeQueryUtility main_voctreeQueryUtility.cpp)

target_link_libraries(aliceVision_utils_voctreeQueryUtility
	aliceVision_voctree
	${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_voctreeQueryUtility
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_voctreeQueryUtility
	DESTINATION bin/
)

# Voctree statistics

add_executable(aliceVision_utils_voctreeStatistics main_voctreeStatistics.cpp)

target_link_libraries(aliceVision_utils_voctreeStatistics
	aliceVision_voctree
	${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_voctreeStatistics
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_voctreeStatistics
	DESTINATION bin/
)


# Frustrum filtering

add_executable(aliceVision_utils_frustumFiltering main_frustumFiltering.cpp)

target_link_libraries(aliceVision_utils_frustumFiltering
  aliceVision_system
  aliceVision_feature
  aliceVision_sfm
  aliceVision_matchingImageCollection
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_frustumFiltering
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_frustumFiltering
  DESTINATION bin/
)

# Transform rig
  
if(ALICEVISION_HAVE_ALEMBIC)
	add_executable(aliceVision_utils_rigTransform main_rigTransform.cpp)

	target_link_libraries(aliceVision_utils_rigTransform
		aliceVision_sfm
		aliceVision_localization
		aliceVision_dataio
		aliceVision_rig
		${Boost_LIBRARIES}
	)
	
	set_property(TARGET aliceVision_utils_rigTransform
		PROPERTY FOLDER Software/Utils
	)

	install(TARGETS aliceVision_utils_rigTransform
		DESTINATION bin/
	)
endif()

# SfM quality evaluation
# - quality comparison against a GT camera path (MultiView Evaluation dataset)

add_executable(aliceVision_utils_qualityEvaluation main_qualityEvaluation.cpp)

target_link_libraries(aliceVision_utils_qualityEvaluation
  aliceVision_system
  aliceVision_feature
  aliceVision_sfm
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_qualityEvaluation
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_qualityEvaluation
  DESTINATION bin/
)

# SfM alignment

add_executable(aliceVision_utils_sfmAlignment main_sfmAlignment.cpp)

target_link_libraries(aliceVision_utils_sfmAlignment
  aliceVision_system
  aliceVision_feature
  aliceVision_sfm
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_sfmAlignment
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_sfmAlignment
  DESTINATION bin/
)

# SfM transform

add_executable(aliceVision_utils_sfmTransform main_sfmTransform.cpp)

target_link_libraries(aliceVision_utils_sfmTransform
  aliceVision_system
  aliceVision_feature
  aliceVision_sfm
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_sfmTransform
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_sfmTransform
  DESTINATION bin/
)

# SfM color harmonize

add_executable(aliceVision_utils_sfmColorHarmonize
  main_sfmColorHarmonize.cpp
  sfmColorHarmonize/colorHarmonizeEngineGlobal.cpp
)

target_link_libraries(aliceVision_utils_sfmColorHarmonize
  aliceVision_system
  aliceVision_image
  aliceVision_kvld
  aliceVision_feature
  aliceVision_colorHarmonization
  aliceVision_sfm
  ${CLP_LIBRARIES}
  ${COINUTILS_LIBRARY}
  ${OSI_LIBRARY}
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_sfmColorHarmonize
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_sfmColorHarmonize
  DESTINATION bin/
)

# SfM alignment

add_executable(aliceVision_utils_sfmLocalization main_sfmLocalization.cpp)

target_link_libraries(aliceVision_utils_sfmLocalization
  aliceVision_system
  aliceVision_feature
  aliceVision_sfm
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_sfmLocalization
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_sfmLocalization
  DESTINATION bin/
)

# Keyframe selection
# - export keyframes from video files / image sequence directories

add_executable(aliceVision_utils_keyframeSelection main_keyframeSelection.cpp)

target_link_libraries(aliceVision_utils_keyframeSelection
  aliceVision_system
  aliceVision_keyframe
  ${OPENIMAGEIO_LIBRARIES}
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_keyframeSelection
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_keyframeSelection
  DESTINATION bin/
)

# Split 360 images in input in order to export square images

add_executable(aliceVision_utils_split360Images main_split360Images.cpp)
target_link_libraries(aliceVision_utils_split360Images
  aliceVision_system
  aliceVision_keyframe
  aliceVision_numeric
  aliceVision_image
  ${OPENIMAGEIO_LIBRARIES}
  ${Boost_LIBRARIES}
)

set_property(TARGET aliceVision_utils_split360Images
  PROPERTY FOLDER Software/Utils
)

install(TARGETS aliceVision_utils_split360Images
  DESTINATION bin/
)
