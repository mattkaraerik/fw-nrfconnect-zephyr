# SPDX-License-Identifier: Apache-2.0

zephyr_library_include_directories(${ZEPHYR_BASE}/drivers)

zephyr_cc_option(-mcpu=${GCC_M_CPU})
zephyr_cc_option(-mno-sdata -mdiv-rem -mswap -mnorm)
zephyr_cc_option(-mmpy-option=6 -mbarrel-shifter)
zephyr_cc_option_ifdef(CONFIG_SOC_EMSK_EM7D --param l1-cache-size=16384)
zephyr_cc_option_ifdef(CONFIG_SOC_EMSK_EM7D --param l1-cache-line-size=32)
zephyr_cc_option_ifdef(CONFIG_SOC_EMSK_EM11D --param l1-cache-size=16384)
zephyr_cc_option_ifdef(CONFIG_SOC_EMSK_EM11D --param l1-cache-line-size=32)
zephyr_cc_option_ifdef(CONFIG_CODE_DENSITY -mcode-density)
zephyr_cc_option_ifdef(CONFIG_FLOAT -mfpu=fpuda_all)


zephyr_sources(
  soc.c
  soc_config.c
  )
