
#把.当前路径下的所有源文件放入变量名SRC_LIST下
aux_source_directory(. SRC_LIST)
aux_source_directory(./db DB_LIST)
aux_source_directory(./model MODEL_LIST)
aux_source_directory(./redis REDIS_LIST)

# 手动指定 MySQL 库的路径（关键新增）
link_directories(/usr/lib64/mysql/) 

#表示server由SRC_list定义的源文件编译而来
add_executable(ChatServer ${SRC_LIST} ${DB_LIST} ${MODEL_LIST} ${REDIS_LIST})

#表示server需要链接的库文件
target_link_libraries(ChatServer muduo_net muduo_base mysqlclient hiredis pthread)