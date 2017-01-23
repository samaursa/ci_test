include_directories(${GAME_SUPERBUILD_DIR}/install/catch/include)

add_library(Math
  "include/Vector.h"
  "include/Vector.cpp"
  )

add_executable(MathTest
  "include/VectorTest.cpp"
  )

target_link_libraries(MathTest Math)

install(TARGETS Math MathTest 
  RUNTIME DESTINATION "bin/" 
  LIBRARY DESTINATION "lib/"
  ARCHIVE DESTINATION "lib/static"
)

add_test(math_test MathTest)
