# Core sources
file(GLOB_RECURSE DEVICE_SOURCES
    "${CMAKE_CURRENT_LIST_DIR}/src/*.c"
    "${CMAKE_CURRENT_LIST_DIR}/devices/*.c"
)

# Collect all device directories for private include paths
file(GLOB DEVICE_DIRS
    RELATIVE ${CMAKE_CURRENT_LIST_DIR}
    "${CMAKE_CURRENT_LIST_DIR}/devices/*"
)

# Convert device directories to absolute paths
set(DEVICE_PRIV_INCLUDE_DIRS "")
foreach(dir ${DEVICE_DIRS})
    if(IS_DIRECTORY "${CMAKE_CURRENT_LIST_DIR}/${dir}")
        list(APPEND DEVICE_PRIV_INCLUDE_DIRS
            "${CMAKE_CURRENT_LIST_DIR}/${dir}"
        )
    endif()
endforeach()

idf_component_register(
    SRCS
        ${DEVICE_SOURCES}

    INCLUDE_DIRS
        "include"

    PRIV_INCLUDE_DIRS
        "src"
        ${DEVICE_PRIV_INCLUDE_DIRS}

    REQUIRES
        esp_lcd
		esp-lcd-ili9486

)