# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20.0)

find_package(Zephyr HINTS $ENV{ZEPHYR_BASE})
project(bsim_test_bis)

if(CONFIG_BT_PER_ADV_SYNC_TRANSFER_SENDER)
target_sources(app PRIVATE
	src/main.c
	src/test_past.c
)
else()
target_sources(app PRIVATE
	src/main.c
	src/test_bis.c
)
endif()

zephyr_include_directories(
  ${ZEPHYR_BASE}
  ${BSIM_COMPONENTS_PATH}/libUtilv1/src/
  ${BSIM_COMPONENTS_PATH}/libPhyComv1/src/
  ${ZEPHYR_BASE}/subsys/bluetooth/controller/include
  )
