cmake_minimum_required(VERSION 2.8.12)

project(helpdeco)

include(CheckIncludeFile)

check_include_file(dir.h HAVE_DIR_H)

add_executable(helpdeco
  HELPDECO.C
  HELPDEC1.C
  HELPDECO.H
)
if(MSVC)
  target_compile_definitions(helpdeco
    PRIVATE
      _CRT_SECURE_NO_WARNINGS
      _CRT_NONSTDC_NO_WARNINGS
  )
endif()

add_executable(splitmrb
  SPLITMRB.C
)
if(MSVC)
  target_compile_definitions(splitmrb
    PRIVATE
      _CRT_SECURE_NO_WARNINGS
      _CRT_NONSTDC_NO_WARNINGS
  )
endif()

add_executable(zapres
  ZAPRES.C
)
if(MSVC)
  target_compile_definitions(zapres
    PRIVATE
      _CRT_SECURE_NO_WARNINGS
      _CRT_NONSTDC_NO_WARNINGS
    )
endif()
if(HAVE_DIR_H)
  target_compile_definitions(zapres PRIVATE HAVE_DIR_H)
endif()
