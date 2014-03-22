cmake_minimum_required(VERSION 2.8)
project(modern_gl_camera)

# Additional packages
  
find_package(GLUT)
find_package(OpenGL)
find_package(GLEW)
#find_package(GLM)
include_directories( ${FREEGLUT_INC_PATH})
include_directories( ${GLEW_INCLUDE_DIRS} )
#include_directories( ${GLM_INCLUDE_DIRS} )


# Add executables
ADD_EXECUTABLE(example example.cpp camera.cpp )
    TARGET_LINK_LIBRARIES(example	
	${FREEGLUT_LIB}
	${GLUT_LIBRARY}
	${OPENGL_LIBRARIES}
	${GLEW_LIBRARIES}
	)
