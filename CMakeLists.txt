#
# Copyright (c) 2023, Telink
#
# SPDX-License-Identifier: Apache-2.0
#

if (CONFIG_OPENTHREAD_TELINK_LIBRARY)

	zephyr_include_directories(
		${CMAKE_CURRENT_SOURCE_DIR}/include
	)

	if (CONFIG_SOC_RISCV_TELINK_B91)
		zephyr_link_libraries(
			${CMAKE_CURRENT_SOURCE_DIR}/lib/libopenthread-ftd-b91.a
		)
	elseif (CONFIG_SOC_RISCV_TELINK_B92)
		zephyr_link_libraries(
			${CMAKE_CURRENT_SOURCE_DIR}/lib/libopenthread-ftd-b92.a
		)
	else()
		message( FATAL_ERROR "Not supported SOC" )
	endif() # CONFIG_SOC_RISCV_TELINK_

endif() # CONFIG_OPENTHREAD_TELINK_LIBRARY
