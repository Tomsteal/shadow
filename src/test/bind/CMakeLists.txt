## build the test as a dynamic executable that plugs into shadow
add_library(shadow-plugin-test-bind SHARED shd-test-bind.c)

## create and install an executable that can run outside of shadow
add_executable(test-bind shd-test-bind.c)

## register the tests
add_test(NAME bind COMMAND test-bind)
add_test(NAME bind-shadow COMMAND ${CMAKE_BINARY_DIR}/src/main/shadow -l debug -d bind.shadow.data ${CMAKE_CURRENT_SOURCE_DIR}/bind.test.shadow.config.xml)
