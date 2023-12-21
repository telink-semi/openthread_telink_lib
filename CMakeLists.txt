#
# Copyright (c) 2023, Telink
#
# SPDX-License-Identifier: Apache-2.0
#

if (CONFIG_OPENTHREAD_TELINK_LIBRARY)

	zephyr_include_directories(
		${CMAKE_CURRENT_SOURCE_DIR}/include
	)

	if (CONFIG_OPENTHREAD_TELINK_LIBRARY_VERSION_EXTENDED)
		zephyr_link_libraries(
			${CMAKE_CURRENT_SOURCE_DIR}/lib/libopenthread-ftd-extended.a
		)
	elseif(CONFIG_OPENTHREAD_TELINK_LIBRARY_VERSION_REDUCED)
		zephyr_link_libraries(
			${CMAKE_CURRENT_SOURCE_DIR}/lib/libopenthread-ftd-reduced.a
		)
	else()
		message( FATAL_ERROR "Unknown Telink library version" )
	endif() # CONFIG_OPENTHREAD_TELINK_LIBRARY_VERSION

	add_library(ot-config INTERFACE)

endif() # CONFIG_OPENTHREAD_TELINK_LIBRARY
