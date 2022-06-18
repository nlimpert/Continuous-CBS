cmake_minimum_required(VERSION 3.5)
project(CCBS)

# Default to C99
if(NOT CMAKE_C_STANDARD)
  set(CMAKE_C_STANDARD 99)
endif()

# Default to C++14
if(NOT CMAKE_CXX_STANDARD)
  set(CMAKE_CXX_STANDARD 14)
endif()

if(CMAKE_COMPILER_IS_GNUCXX OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
  add_compile_options(-Wall -Wextra -Wpedantic)
endif()

# find dependencies
find_package(ament_cmake REQUIRED)
# uncomment the following section in order to fill in
# further dependencies manually.
# find_package(<dependency> REQUIRED)

set( SOURCE_FILES
     main.cpp
   config.cpp
     tinyxml2.cpp
     xml_logger.cpp
     map.cpp
     heuristic.cpp
     sipp.cpp
     task.cpp
     cbs.cpp
   simplex/columnset.cpp
   simplex/constraint.cpp
   simplex/matrix.cpp
   simplex/objectivefunction.cpp
   simplex/simplex.cpp
   simplex/variable.cpp)

set( HEADER_FILES
     const.h
     tinyxml2.h
   config.h
     xml_logger.h
     map.h
     heuristic.h
     sipp.h
     task.h
     cbs.h
   structs.h
   simplex/columnset.h
   simplex/constraint.h
   simplex/datamismatchexception.h
   simplex/divisionbyzeroexception.h
   simplex/indexoutofboundexception.h
   simplex/matrix.h
   simplex/matrixissingularexception.h
   simplex/matrixnotsquareexception.h
     simplex/memoryreachedoutexception.h
     simplex/notavectorexception.h
     simplex/objectivefunction.h
     simplex/pilal.h
     simplex/pilalexceptions.h
   simplex/simplex.h
   simplex/simplexexceptions.h
   simplex/sizemismatchexception.h
   simplex/variable.h)

add_executable( CCBS ${SOURCE_FILES} ${HEADER_FILES} )

if(BUILD_TESTING)
  find_package(ament_lint_auto REQUIRED)
  # the following line skips the linter which checks for copyrights
  # uncomment the line when a copyright and license is not present in all source files
  #set(ament_cmake_copyright_FOUND TRUE)
  # the following line skips cpplint (only works in a git repo)
  # uncomment the line when this package is not in a git repo
  #set(ament_cmake_cpplint_FOUND TRUE)
  ament_lint_auto_find_test_dependencies()
endif()

ament_package()
