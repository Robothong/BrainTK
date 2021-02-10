cmake_minimum_required(VERSION 3.5)

project(BrainTK LANGUAGES CXX)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

<<<<<<< HEAD
INCLUDE_DIRECTORIES(/usr/local/include/vtk-9.0)
INCLUDE_DIRECTORIES(/usr/local/include/ITK-5.1)
INCLUDE_DIRECTORIES(/usr/local/include/opencv4)
INCLUDE_DIRECTORIES(/usr/local/include/dcmtk)
INCLUDE_DIRECTORIES(/usr/local/include/ctk-0.1)
# INCLUDE_DIRECTORIES(/usr/include/linux)
# INCLUDE_DIRECTORIES(/usr/include/c++/9)

link_directories("/usr/lib" "/usr/lib/x86_64-linux-gnu" "/usr/local/lib")

=======
>>>>>>> a70a6c00387d8337b4038372312d3f74ff6b549c
# QtCreator supports the following variables for Android, which are identical to qmake Android variables.
# Check http://doc.qt.io/qt-5/deployment-android.html for more information.
# They need to be set before the find_package(Qt5 ...) call.

#if(ANDROID)
#    set(ANDROID_PACKAGE_SOURCE_DIR "${CMAKE_CURRENT_SOURCE_DIR}/android")
#    if (ANDROID_ABI STREQUAL "armeabi-v7a")
#        set(ANDROID_EXTRA_LIBS
#            ${CMAKE_CURRENT_SOURCE_DIR}/path/to/libcrypto.so
#            ${CMAKE_CURRENT_SOURCE_DIR}/path/to/libssl.so)
#    endif()
#endif()

find_package(Qt5 COMPONENTS Widgets LinguistTools REQUIRED)

set(TS_FILES BrainTK_zh_CN.ts)

if(ANDROID)
  add_library(BrainTK SHARED
    main.cpp
    mainwindow.cpp
    mainwindow.h
    mainwindow.ui
    ${TS_FILES}
  )
else()
  add_executable(BrainTK
    main.cpp
    mainwindow.cpp
    mainwindow.h
    mainwindow.ui
    ${TS_FILES}
  )
endif()

target_link_libraries(BrainTK PRIVATE Qt5::Widgets)

qt5_create_translation(QM_FILES ${CMAKE_SOURCE_DIR} ${TS_FILES})
