######################################################
# TESTS

set(BT_MTC_TESTS
  gtest_mtc_properties.cpp
  gtest_mtc_modify_planning_scene.cpp
  gtest_plan_mtc_task.cpp
)

set(TEST_DEPENDECIES
    gtest_utils
    ${PROJECT_NAME}
)

if(CATKIN_ENABLE_TESTING)
    find_package(rostest REQUIRED)




    add_library(gtest_utils models.cpp stage_mockups.cpp)
    target_link_libraries(gtest_utils ${PROJECT_NAME})

    catkin_add_gtest(${PROJECT_NAME}_test ${BT_MTC_TESTS})
    target_link_libraries(${PROJECT_NAME}_test
        ${TEST_DEPENDECIES}
        ${catkin_LIBRARIES})

endif()
