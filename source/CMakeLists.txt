add_library(libiosuhax
    ${CMAKE_CURRENT_SOURCE_DIR}/iosuhax.c
    ${CMAKE_CURRENT_SOURCE_DIR}/iosuhax_cfw.c
    ${CMAKE_CURRENT_SOURCE_DIR}/iosuhax_devoptab.c
    ${CMAKE_CURRENT_SOURCE_DIR}/iosuhax_disc_interface.c
)
add_library(libiosuhax::libiosuhax ALIAS libiosuhax)

target_include_directories(libiosuhax
    PUBLIC
        ${PROJECT_SOURCE_DIR}/include
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}
)
