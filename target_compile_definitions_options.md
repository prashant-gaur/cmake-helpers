target_compile_definitions
==========================
Specifies compile definitions to use when compiling a given application or library.


CMakeLists.txt

    # Disabled by default
    option("ENABLE_FEATURE"          "Enable feature"                OFF)

    if(ENABLE_FEATURE)
      target_compile_definitions(${target_name} PRIVATE APP_XYZ_FEATURE)
       else()
    ...
    endif()

    here, ${target_name} can be ${CMAKE_PROJECT_NAME}

Source.cc

    #if defined(APP_XYZ_FEATURE)
    ...
    #endif

Driver code can be bitbake recipe

MyApp.bb

    EXTRA_OECMAKE += " -DENABLE_FEATURE=ON"
    or
    CXXFLAGS += " -DAPP_XYZ_FEATURE"


target_compile_options
======================
This is used to add compiler(gcc/g++) related options like -Wall -pthread etc

    target_compile_options(
        ${target_name} PRIVATE -pthread -Wall -Wextra -Werror)