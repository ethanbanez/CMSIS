target_sources(${STM32CMSIS_TEMPLATES}
    PUBLIC
        system_stm32h7xx.c
        system_stm32h7xx_singlecore.c
    PRIVATE
        gcc/startup_stm32h743xx.s   # template startup code
)