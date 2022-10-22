set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(PROJECT_NAME Timer)

# find boost
set(Boost_USE_STATIC_LIBS ON)
set(Boost_USE_MULTITHREADED ON)
set(Boost_USE_STATIC_RUNTIME OFF)

set(EXECUTABLE_OUTPUT_PATH "K:/work/TestBoost/bin")

get_filename_component(BOOST_DIR "../../SDK/boost_1_79_0" ABSOLUTE)
set(BOOST_ROOT ${BOOST_DIR} CACHE PATH "The default path to Boost directory")

find_package(Boost 1.79 REQUIRED)

message(STATUS "Boost version: ${Boost_VERSION}")

if(Boost_FOUND)
	add_executable(${PROJECT_NAME} "Main.cpp")
	target_include_directories(${PROJECT_NAME} PRIVATE ${Boost_INCLUDE_DIRS})
	target_link_libraries(${PROJECT_NAME} PRIVATE ${Boost_LIBRARIES})	
endif()

