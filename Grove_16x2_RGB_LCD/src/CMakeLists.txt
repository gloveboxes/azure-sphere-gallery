#  Copyright (c) Microsoft Corporation. All rights reserved.
#  Licensed under the MIT License.

cmake_minimum_required(VERSION 3.10)

project(Grove16x2RGBLCD_HighLevelApp C)

azsphere_configure_tools(TOOLS_REVISION "21.04")
azsphere_configure_api(TARGET_API_SET "9")

add_executable(${PROJECT_NAME} 
	main.c 
	utils.c
	16x2_driver/rgb_lcd.c
)

target_link_libraries(${PROJECT_NAME} applibs gcc_s c)

# Referencing the HardwareDefinitions directly from the SDK, so to not carry them over
azsphere_target_hardware_definition(${PROJECT_NAME} TARGET_DIRECTORY "${AZURE_SPHERE_SDK_PATH}/HardwareDefinitions" TARGET_DEFINITION "mt3620_rdb.json")

azsphere_target_add_image_package(${PROJECT_NAME})
