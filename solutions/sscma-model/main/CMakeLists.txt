file(GLOB_RECURSE srcs ${CMAKE_CURRENT_LIST_DIR}/*.c ${CMAKE_CURRENT_LIST_DIR}/*.cpp)

set(incs ${CMAKE_CURRENT_LIST_DIR}
    ${CMAKE_CURRENT_LIST_DIR}/node
)

message(STATUS "SOURCES: ${SOURCES}")

component_register(
    COMPONENT_NAME main
    SRCS ${srcs}
    INCLUDE_DIRS ${incs}
    PRIVATE_REQUIREDS sscma cvi_rtsp  opencv_core opencv_imgcodecs opencv_imgproc
)
set(OpenCV_LIB_PATH "${CMAKE_SOURCE_DIR}/lib") # 静态库路径
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_core.so.3.2.0)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_imgproc.so.3.2.0)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_imgcodecs.so.3.2.0)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_core.so)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_imgproc.so)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_imgcodecs.so)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_features2d.so)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_flann.so)
target_link_libraries(main PRIVATE ${OpenCV_LIB_PATH}/libopencv_calib3d.so)
target_link_libraries(main PRIVATE /ssd_data/sg200x_sdk/sg2002_recamera_emmc/buildroot-2021.05/output/cvitek_CV181X_musl_riscv64/host/riscv64-buildroot-linux-musl/sysroot/usr/lib/libssl.so.1.1)
target_link_libraries(main PRIVATE /ssd_data/sg200x_sdk/sg2002_recamera_emmc/buildroot-2021.05/output/cvitek_CV181X_musl_riscv64/host/riscv64-buildroot-linux-musl/sysroot/usr/lib/libcrypto.so.1.1)
target_link_libraries(main PRIVATE /ssd_data/sg200x_sdk/sg2002_recamera_emmc/buildroot-2021.05/output/cvitek_CV181X_musl_riscv64/host/riscv64-buildroot-linux-musl/sysroot/usr/lib/libjson-c.so.5.1.0)