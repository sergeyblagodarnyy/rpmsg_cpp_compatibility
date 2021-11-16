PROJECT(m4_rpmsg_cpp_compatibility)

cmake_policy(SET CMP0057 NEW)
cmake_policy(SET CMP0076 NEW)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

set(STM32_CUBE_PATH "${STM32_CUBE_MP1_PATH}")
set(FREERTOS_PATH   "${STM32_CUBE_MP1_PATH}/Middlewares/Third_Party/FreeRTOS")
set(OPEN_AMP_PATH "${STM32_CUBE_PATH}/Middlewares/Third_Party/OpenAMP")
set(STM32)
set(STM32_FAMILY "STM32MP1")
find_package(CMSIS COMPONENTS STM32MP157AA)
find_package(HAL COMPONENTS STM32MP1 REQUIRED)
add_compile_definitions(CORE_CM4)
   
set(STM32_FLAGS "${STM32_FLAGS} -mcpu=cortex-m4 -mfpu=fpv4-sp-d16 -mfloat-abi=hard -mthumb -mabi=aapcs")
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} ${STM32_FLAGS}")
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} ${STM32_FLAGS} -fconserve-stack -fno-rtti -fno-exceptions -fno-threadsafe-statics -Wnoexcept")

add_executable(m4_rpmsg_cpp_compatibility 
   empty_main.cpp
   stm32mp1xx_hal_conf.h
)

target_link_libraries(m4_rpmsg_cpp_compatibility
   HAL::STM32::MP1
   HAL::STM32::MP1::RCC
   HAL::STM32::MP1::RCCEx
   HAL::STM32::MP1::GPIO
   HAL::STM32::MP1::CORTEX
   HAL::STM32::MP1::IPCC
   CMSIS::STM32::MP157AA
   STM32::NoSys
)
target_include_directories(
   m4_rpmsg_cpp_compatibility PUBLIC
   ${OPEN_AMP_PATH}/open-amp/lib/include
   ${OPEN_AMP_PATH}/virtual_driver
   ${OPEN_AMP_PATH}/libmetal/lib/include
   ${CMAKE_CURRENT_SOURCE_DIR}
)

