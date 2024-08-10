add_library(stm32cmsis_headers INTERFACE)
target_include_directories(stm32cmsis_headers BEFORE INTERFACE ${CMAKE_CURRENT_LIST_DIR}/Include)



add_library(stm32cmsis_templates STATIC)

set(SRC_PATH_PREFIX Source/Templates/)

target_include_directories(stm32cmsis_templates 
PRIVATE 
$<TARGET_PROPERTY:stm32cmsis_headers,INTERFACE_INCLUDE_DIRECTORIES>
$<TARGET_PROPERTY:armcmsis,INTERFACE_INCLUDE_DIRECTORIES>
)

target_sources(stm32cmsis_templates
    PUBLIC
        ${SRC_PATH_PREFIX}system_stm32h7xx_singlecore.c
    PRIVATE
        ${SRC_PATH_PREFIX}gcc/startup_stm32h743xx.s   # template startup code
)




install(TARGETS stm32cmsis_headers DESTINATION lib)
install(TARGETS stm32cmsis_templates DESTINATION lib)