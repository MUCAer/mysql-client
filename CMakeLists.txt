include(ExternalProject)
set(LIB_MYSQL "mysqlclient")
ExternalProject_Add(ADD_${LIB_MYSQL}
	URL http://cdn.tarsyun.com/src/mysql-connector-c-6.1.11-src.fixed.tar.gz
        DOWNLOAD_DIR ${CMAKE_SOURCE_DIR}/download
        PREFIX ${CMAKE_BINARY_DIR}
        INSTALL_DIR ${CMAKE_SOURCE_DIR}
        CONFIGURE_COMMAND ${CMAKE_COMMAND} .  -DCMAKE_INSTALL_PREFIX=${CMAKE_BINARY_DIR}/src/mysql -DDEFAULT_CHARSET=utf8 -DDEFAULT_COLLATION=utf8_general_ci -DDISABLE_SHARED=1
        SOURCE_DIR ${CMAKE_BINARY_DIR}/src/mysql-lib
        BUILD_IN_SOURCE 1
        BUILD_COMMAND make mysqlclient
        URL_MD5 3578d736b9d493eae076a67e3ed473eb
)
    INSTALL(DIRECTORY ${CMAKE_BINARY_DIR}/src/mysql/lib DESTINATION thirdparty)
    INSTALL(DIRECTORY ${CMAKE_BINARY_DIR}/src/mysql/include/ DESTINATION thirdparty/include/mysql)
