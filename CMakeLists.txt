cmake_minimum_required(VERSION 3.24)
project(QuestionableCode_Module_5_Assignment_)

set(CMAKE_CXX_STANDARD 17)
add_executable(QuestionableCode_Module_5_Assignment_ QuestionableCode.cpp)

find_program(CPPCHECK_EXECUTABLE cppcheck)
if(CPPCHECK_EXECUTABLE)
    set(CPPCHECK_ARGS "--enable=all" "--inconclusive" "--xml" "--xml-version=2" "--output-file=cppcheck_report.xml" "${CMAKE_SOURCE_DIR}")
    add_custom_command(TARGET QuestionableCode_Module_5_Assignment_
            POST_BUILD
            COMMAND ${CPPCHECK_EXECUTABLE} ${CPPCHECK_ARGS}
            COMMENT "Running cppcheck"
            )
else()
    message(WARNING "cppcheck not found, skipping analysis")
endif()



