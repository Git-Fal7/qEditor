cmake_minimum_required (VERSION 3.8.2)
set(PROJECT qEditor)
project(${PROJECT})

# Find includes in the build directories
set(CMAKE_INCLUDE_CURRENT_DIR ON)

# Turn on automatic invocation of the MOC, UIC & RCC
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTORCC ON)

# Add a compiler flag
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall")

# Find the QtWidgets library
find_package(Qt5 REQUIRED COMPONENTS Widgets PrintSupport)

# Tell CMake to create the executable
add_executable(${PROJECT} src/editor.cpp src/main.cpp 
src/documentmetrics.h src/linenumberarea.h

src/finddialog.cpp src/gotodialog.cpp src/language.cpp src/metricreporter.cpp 
 src/searchhistory.cpp src/settings.cpp src/tabbededitor.cpp src/utilityfunctions.cpp

src/highlighters/highlighter.cpp src/highlighters/chighlighter.cpp src/highlighters/cpphighlighter.cpp
 src/highlighters/javahighlighter.cpp src/highlighters/pythonhighlighter.cpp

src/mainwindow.cpp src/mainwindow.ui
)

# Add the Qt5 Widgets for linking
target_link_libraries(${PROJECT} Qt5::Widgets Qt5::PrintSupport)

install(TARGETS ${PROJECT} RUNTIME DESTINATION bin)
install(FILES "resources/qEditor.desktop" DESTINATION "/usr/share/applications")
