project(example1 CXX)

add_executable(example1 example1.cpp)
target_link_libraries(example1 Etaler)

project(spbench CXX)
add_executable(spbench spbench.cpp)
target_link_libraries(spbench Etaler)

project(tmexample CXX)
add_executable(tmexample tmexample.cpp)
target_link_libraries(tmexample Etaler)

project(tmbench CXX)
add_executable(tmbench tmbench.cpp)
target_link_libraries(tmbench Etaler)

if(ETALER_ENABLE_OPENCL)
	project(backend2backend CXX)
	add_executable(backend2backend backend2backend.cpp)
	target_link_libraries(backend2backend Etaler)
endif()

if(ETALER_MKL_DNN_EXAMPLE)
	find_package(MKLDNN REQUIRED)

	if(NOT ${MKLDNN_FOUND})
		message(FATAL_ERROR "Could not locate Intel MKL-DNN")
	else()
		message(STATUS "Found existing Intel MKL-DNN")
	endif()

	project(mkl-dnn_example CXX)
	add_executable(mkl-dnn_example mkl-dnn_example.cpp)
	target_link_libraries(mkl-dnn_example Etaler)
	target_link_libraries(mkl-dnn_example MKLDNN::mkldnn)
endif()
