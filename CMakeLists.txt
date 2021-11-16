PROJECT(m4_rpmsg_cpp_compatibility)

cmake_policy(SET CMP0057 NEW)
cmake_policy(SET CMP0076 NEW)

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
   CMSIS::STM32::MP157AA
   STM32::NoSys
)

