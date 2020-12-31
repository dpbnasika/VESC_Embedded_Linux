#cmake version
cmake_minimum_required(VERSION 3.0)

#specify the project name
project (vesc_uart_app)

#specify the sources to compile
file(GLOB src_cpp_files "bldc.cpp"
"main.cpp"
"bldc_interface.c"
"bldc_interface_uart.c"
"buffer.c"
"timers.c"
"comm_uart.c"
"crc.c"
"packet.c")

# include the headers directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/*.h)

#add system related flags
add_definitions(-lrt)
add_definitions(-std=c++11)
add_definitions(-w)
add_definitions(-fPIC)


#create an executable for the sources
add_executable(vesc_uart_app ${src_cpp_files} ${src_c_files})

#link all the system related libraries
target_link_libraries(vesc_uart_app -ldl)
target_link_libraries(vesc_uart_app -lrt)
