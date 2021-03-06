OPTION(COCOS2D_X_V2 "Build for cocos2d-x v2.x" OFF)
OPTION(COCOS2D_X_V3 "Build for cocos2d-x v3.x" OFF)

INCLUDE(wrapper/CMakeLists.txt)

SET(CrossLayout_SRC
		${WRAPPER_SRC}
		src/crosslayout/Composer.cpp src/crosslayout/Composer.h
		src/crosslayout/geometry/GeometryToString.h
		src/crosslayout/geometry/Point.cpp src/crosslayout/geometry/Point.h
		src/crosslayout/geometry/Rect.cpp src/crosslayout/geometry/Rect.h
		src/crosslayout/geometry/Size.cpp src/crosslayout/geometry/Size.h
		src/crosslayout/layout/Linear.cpp src/crosslayout/layout/Linear.h
		src/crosslayout/layout/Margin.h
		src/crosslayout/NodeGroup.h
		src/crosslayout/NodeWrapper.h
		src/crosslayout/NodeWrapperPlain.h
		src/crosslayout/Pixel.cpp src/crosslayout/Pixel.h
		)

# BUILD_SHARED_LIBS can controll build type!
ADD_LIBRARY(CrossLayout ${CrossLayout_SRC})

TARGET_COMPILE_OPTIONS(CrossLayout PRIVATE
		-Wall -pedantic
		-Wnon-virtual-dtor
		#-Werror
		)

IF(TARGET gtest)
	ADD_SUBDIRECTORY(test/)
ENDIF()

TARGET_INCLUDE_DIRECTORIES(CrossLayout PUBLIC
		src/
		${WRAPPER_INCLUDE}
		)
