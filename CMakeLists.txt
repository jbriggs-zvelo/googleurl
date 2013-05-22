CMAKE_MINIMUM_REQUIRED(VERSION 2.8.7)
PROJECT(googleurl)

SET(SOURCES
  base/string16.cc
  src/gurl.cc
  src/url_canon_etc.cc
  src/url_canon_fileurl.cc
  src/url_canon_filesystemurl.cc
  src/url_canon_host.cc
  src/url_canon_icu.cc
  src/url_canon_internal.cc
  src/url_canon_ip.cc
  src/url_canon_mailtourl.cc
  src/url_canon_path.cc
  src/url_canon_pathurl.cc
  src/url_canon_query.cc
  src/url_canon_relative.cc
  src/url_canon_stdurl.cc
  src/url_parse.cc
  src/url_parse_file.cc
  src/url_util.cc
)

INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR})
INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR}/..)
INCLUDE_DIRECTORIES(${ICU_INCLUDE_DIR})

SET(EXTERNAL_LIBRARIES
  ${ICU_LIBRARY_DIR}/libicudata.a
  ${ICU_LIBRARY_DIR}/libicui18n.a
  ${ICU_LIBRARY_DIR}/libicuuc.a
)

ADD_LIBRARY(googleurl ${SOURCES})
TARGET_LINK_LIBRARIES(googleurl ${EXTERNAL_LIBRARIES})


INSTALL(
  TARGETS googleurl
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  PUBLIC_HEADER DESTINATION include/googleurl)

#SET(EXEC_SOURCES
#  src/gurl_test_main.cc
#  src/gurl_unittest.cc
#  src/url_canon_unittest.cc
#  src/url_parse_unittest.cc
#  src/url_util_unittest.cc
#)
#
#ADD_EXECUTABLE(googleurl-test ${EXEC_SOURCES})
#TARGET_LINK_LIBRARIES(googleurl-test googleurl)
#
#ADD_TEST(
#  NAME googleurl-test
#  COMMAND googleurl-test
#)