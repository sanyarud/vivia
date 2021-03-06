project(vgVtkVideo)

set(vgVtkVideoSources
  vgVideoAnimation.cxx
  vgVideoSeekRequest.cxx
  vgVideoPlayer.cxx
  vgVideoPlayerBufferedRequestor.cxx
  vgVideoPlayerRequestor.cxx
  vgVideoRequestor.cxx
  vgVideoSourceRequestor.cxx
)

set(vgVtkVideoInstallHeaders
  vgVideoAnimation.h
  vgVideoPlayer.h
  vgVideoRequestor.h
  vgVideoSource.h
  vgVideoSourceRequestor.h
  vgVtkVideoFrame.h
)

include_directories(SYSTEM
  ${VTK_INCLUDE_DIRS}
)

add_library(${PROJECT_NAME} ${vgVtkVideoSources})

target_link_libraries(${PROJECT_NAME}
  PUBLIC
  qtExtensions
  vgVideo
  vtkVgCore
  vtkVgVideo
  vtkRenderingCore
  ${VTK_JPEG_LIBRARIES}
  PRIVATE
  vgl
  vgl_algo
)

install_library_targets(${PROJECT_NAME})
install_headers(${vgVtkVideoInstallHeaders} TARGET ${PROJECT_NAME}
                DESTINATION include/VgVtkVideo)
