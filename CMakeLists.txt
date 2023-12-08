#
# Copyright (c) 2023, Telink
#
# SPDX-License-Identifier: Apache-2.0
#

if (CONFIG_OPENTHREAD_TELINK_LIBRARY)

	zephyr_include_directories(
		${CMAKE_CURRENT_SOURCE_DIR}/include
	)


	zephyr_link_libraries(
		${CMAKE_CURRENT_SOURCE_DIR}/lib/libopenthread-ftd.a
	)

endif() # CONFIG_OPENTHREAD_TELINK_LIBRARY
