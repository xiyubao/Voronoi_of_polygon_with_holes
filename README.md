# Voronoi_of_polygon_with_holes

## 1. move files from BOOST.POLYGON

mkdir *project_name*
cd *project_name*
copy "voronoi_visual_utils.hpp" "voronoi_visualizer.hpp" into *project_name*

## 2. setup vscode files
edit *project_name*/.vscode/c_cpp_properities.json
edit *project_name*/.vscode/task.json

## 3.compile
add
#include <QApplication>
#include <QMainWindow>
#include <QMessageBox>
#include <QHBoxLayout>
#include <QFileDialog>
#include <QListWidget>
#include <QLabel>
#include <QPushButton>
#include <QCheckBox>
#include <QtCore/qcoreapplication.h>
to voronoi_visualizer.cpp


qmake -project
edge *project_name*/*project_name*.pro

INCLUDEPATH += /usr/local/include
LIBS += -L/usr/local/lib/x86_64-linux-gnu -lboost_system -lboost_thread -lboost_timer
QT += gui widgets opengl
CONFIG += debug

qmake *project_name*.pro

auto generate Makefile

make

auto generate voronoi_visualizer.moc and moc_predefs.h

chmod +x *project_name*

./*project_name*


## 4.Debug
create launch.json







## c_cpp_properties.json
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**",
                "/usr/include/x86_64-linux-gnu/qt5/QtWidgets",
                "/usr/include/x86_64-linux-gnu/qt5/QtOpenGL",
                "/usr/include/x86_64-linux-gnu/qt5/*",
                "/usr/local/include",
                "/usr/local/include/boost",
                "/usr/local/include/boost/geometry",
                "${workspaceFolder}"
            ],
            "defines": [],
            "cStandard": "c17",
            "cppStandard": "c++14",
            "intelliSenseMode": "linux-clang-x64"
        }
    ],
    "version": 4
}

## launch.json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Debug",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/test4",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "make"
        }
    ]
}

## setting.json
{
    "C_Cpp.errorSquiggles": "disabled",
    "files.associations": {
        "cctype": "cpp",
        "clocale": "cpp",
        "cmath": "cpp",
        "cstdarg": "cpp",
        "cstddef": "cpp",
        "cstdio": "cpp",
        "cstdlib": "cpp",
        "cstring": "cpp",
        "ctime": "cpp",
        "cwchar": "cpp",
        "cwctype": "cpp",
        "array": "cpp",
        "atomic": "cpp",
        "strstream": "cpp",
        "bit": "cpp",
        "*.tcc": "cpp",
        "bitset": "cpp",
        "cfenv": "cpp",
        "charconv": "cpp",
        "chrono": "cpp",
        "complex": "cpp",
        "condition_variable": "cpp",
        "cstdint": "cpp",
        "deque": "cpp",
        "list": "cpp",
        "map": "cpp",
        "set": "cpp",
        "unordered_map": "cpp",
        "unordered_set": "cpp",
        "vector": "cpp",
        "exception": "cpp",
        "algorithm": "cpp",
        "functional": "cpp",
        "iterator": "cpp",
        "memory": "cpp",
        "memory_resource": "cpp",
        "numeric": "cpp",
        "optional": "cpp",
        "random": "cpp",
        "ratio": "cpp",
        "source_location": "cpp",
        "string": "cpp",
        "string_view": "cpp",
        "system_error": "cpp",
        "tuple": "cpp",
        "type_traits": "cpp",
        "utility": "cpp",
        "fstream": "cpp",
        "future": "cpp",
        "initializer_list": "cpp",
        "iomanip": "cpp",
        "iosfwd": "cpp",
        "iostream": "cpp",
        "istream": "cpp",
        "limits": "cpp",
        "mutex": "cpp",
        "new": "cpp",
        "ostream": "cpp",
        "shared_mutex": "cpp",
        "sstream": "cpp",
        "stdexcept": "cpp",
        "streambuf": "cpp",
        "thread": "cpp",
        "cinttypes": "cpp",
        "typeindex": "cpp",
        "typeinfo": "cpp",
        "valarray": "cpp",
        "variant": "cpp",
        "qcheckbox": "cpp",
        "codecvt": "cpp",
        "*.moc": "cpp",
        "qapplication": "cpp",
        "qpushbutton": "cpp"
    }
}

## task.json (moc)
{
    "tasks": [
        {
            "label": "moc",
            "type": "shell",
            "command": "moc",
            "args": [
                "${workspaceFolder}/voronoi_visualizer.cpp",
                "-o",
                "${workspaceFolder}/voronoi_visualizer.moc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        },
        {
            "type": "cppbuild",
            "label": "C/C++: g++ build active file",
            "command": "/usr/bin/g++",
            "args": [
                "-fdiagnostics-color=always",
                "-g",
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}",
                "-I",
                "usr/local/include/boost",
                "-I",
                "usr/local/include"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "detail": "Task generated by Debugger."
        }
    ],
    "version": "2.0.0"
}

## task.json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "qmake",
            "type": "shell",
            "command": "qmake",
            "group": "build"
        },
        {
            "label": "make",
            "type": "shell",
            "command": "make",
            "group": "build",
            "dependsOn": "qmake"
        },
        {
            "type": "cppbuild",
            "label": "C/C++: g++ build active file",
            "command": "/usr/bin/g++",
            "args": [
                "-fdiagnostics-color=always",
                "-g",
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "detail": "Task generated by Debugger."
        }
    ]
}

## XXX.pro
######################################################################
# Automatically generated by qmake (3.1) Mon Dec 4 13:21:23 2023
######################################################################

TEMPLATE = app
TARGET = test4
INCLUDEPATH += /usr/local/include
LIBS += -L/usr/local/lib/x86_64-linux-gnu -lboost_system -lboost_thread -lboost_timer
QT += gui widgets opengl
CONFIG += debug


# The following define makes your compiler warn you if you use any
# feature of Qt which has been marked as deprecated (the exact warnings
# depend on your compiler). Please consult the documentation of the
# deprecated API in order to know how to port your code away from it.
DEFINES += QT_DEPRECATED_WARNINGS

# You can also make your code fail to compile if you use deprecated APIs.
# In order to do so, uncomment the following line.
# You can also select to disable deprecated APIs only up to a certain version of Qt.
#DEFINES += QT_DISABLE_DEPRECATED_BEFORE=0x060000    # disables all the APIs deprecated before Qt 6.0.0

# Input
HEADERS += algorithm.hpp \
           bezier.hpp \
           concavehull.hpp \
           convexhull.hpp \
           delaunator.hpp \
           earcut.hpp \
           extend.hpp \
           generator_int64.h \
           hvd.hpp \
           Inward_denting.hpp \
           Macro.h \
           point_int64.h \
           polypartition.hpp \
           site.hpp \
           voronoi_advanced.hpp \
           voronoi_visual_utils.hpp
SOURCES += algorithm.cpp \
           bezier.cpp \
           concavehull.cpp \
           convexhull.cpp \
           delaunator.cpp \
           extend.cpp \
           hvd.cpp \
           Inward_denting.cpp \
           point_int64.cpp \
           polypartition.cpp \
           site.cpp \
           voronoi_visualizer.cpp
