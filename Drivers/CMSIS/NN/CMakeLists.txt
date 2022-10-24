project(cmsis_nn)

set(CMSIS_NN_DIRECTORIES
    ${CMAKE_CURRENT_LIST_DIR}/Include
)

set(CMSIS_NN_SOURCES
    ${CMAKE_CURRENT_LIST_DIR}/Source/ActivationFunctions/arm_nn_activations_q7.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ActivationFunctions/arm_nn_activations_q15.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ActivationFunctions/arm_relu_q7.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ActivationFunctions/arm_relu_q15.c

    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_1x1_HWC_q7_fast_nonsquare.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q7_basic_nonsquare.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q7_basic.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q7_fast_nonsquare.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q7_fast.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q7_RGB.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q15_basic.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q15_fast_nonsquare.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_convolve_HWC_q15_fast.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_depthwise_separable_conv_HWC_q7_nonsquare.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_depthwise_separable_conv_HWC_q7.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_nn_mat_mult_kernel_q7_q15_reordered.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/ConvolutionFunctions/arm_nn_mat_mult_kernel_q7_q15.c

    ${CMAKE_CURRENT_LIST_DIR}/Source/FullyConnectedFunctions/arm_fully_connected_mat_q7_vec_q15_opt.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/FullyConnectedFunctions/arm_fully_connected_mat_q7_vec_q15.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/FullyConnectedFunctions/arm_fully_connected_q7_opt.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/FullyConnectedFunctions/arm_fully_connected_q7.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/FullyConnectedFunctions/arm_fully_connected_q15_opt.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/FullyConnectedFunctions/arm_fully_connected_q15.c

    ${CMAKE_CURRENT_LIST_DIR}/Source/NNSupportFunctions/arm_nn_mult_q7.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/NNSupportFunctions/arm_nn_mult_q15.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/NNSupportFunctions/arm_nntables.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/NNSupportFunctions/arm_q7_to_q15_no_shift.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/NNSupportFunctions/arm_q7_to_q15_reordered_no_shift.c

    ${CMAKE_CURRENT_LIST_DIR}/Source/PoolingFunctions/arm_pool_q7_HWC.c

    ${CMAKE_CURRENT_LIST_DIR}/Source/SoftmaxFunctions/arm_softmax_q7.c
    ${CMAKE_CURRENT_LIST_DIR}/Source/SoftmaxFunctions/arm_softmax_q15.c
)

add_library(${PROJECT_NAME} EXCLUDE_FROM_ALL ${CMSIS_NN_SOURCES})
add_library(cmsis_nn::lib ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_NN_DIRECTORIES}
)

target_sources(${PROJECT_NAME}
    PUBLIC
        ${CMSIS_NN_DIRECTORIES}
    PRIVATE
        ${CMSIS_NN_SOURCES}
)
