
cmake_minimum_required(VERSION 2.8)
project(word2vec)

# Flags from original makefile
# CFLAGS = -lm -pthread -O3 -march=native -Wall -funroll-loops -Wno-unused-result

find_package (Threads)
find_package (MATH)

IF(UNIX)
  set(MATH_LIB m)
ENDIF(UNIX)

set(LIBRARIES ${CMAKE_THREAD_LIBS_INIT} ${MATH_LIB})

add_executable(word2vec word2vec.c)
target_link_libraries(word2vec ${LIBRARIES})

add_executable(word2phrase word2phrase.c)
target_link_libraries(word2phrase ${LIBRARIES})

add_executable(distance distance.c)
target_link_libraries(distance ${LIBRARIES})

add_executable(word-analogy word-analogy.c)
target_link_libraries(word-analogy ${LIBRARIES})

add_executable(compute-accuracy compute-accuracy.c)
target_link_libraries(compute-accuracy ${LIBRARIES})
