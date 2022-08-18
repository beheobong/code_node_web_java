- insert query: - https://www.mysqltutorial.org/mysql-insert-statement.aspx

### 1. this is incompatible with sql_mode=only_full_group_by
- https://stackoverflow.com/a/36033983

### 2. Sequelize Aggregate Functions (MIN, MAX, SUM, COUNT, etc.) Examples
- https://www.woolha.com/tutorials/sequelize-aggregate-functions-sum-count-min-max-etc-examples

### CentOS 7 cho phép remote đến mysql database
Nhật Đặng Thanh / 03/06/2021
Bời vì server mặc định không mở port 3306

1 – Đầu tiên cần public port 3306

```
sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload
```

2 – Cài đặt remote login user và password
chạy câu lệnh command line:

```
mysql> GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY '12345678' WITH GRANT OPTION;


mysql> flush privileges;
```

NOTE:
root là username,% nghĩa là tất cả máy khác đều có thể kết nối, hoặc có thể đặt cố định 1 địa chỉ IP, 12345678 là password
