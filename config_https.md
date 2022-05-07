https://stackoverflow.com/a/52007971
https://github.com/sagardere/set-up-SSL-in-nodejs
- https://github.com/sindresorhus/guides/blob/main/run-node-server-alongside-apache.md


*Môi trường linux
Yêu cầu cài certbot
Yêu cầu cài apache
- B1: truy cập theo đường dẫn /etc/httpd/conf.d
- B2: tạo file conf Vd: example.com.conf
- B2: Tạo VirtualHost tương ứng VD
<VirtualHost *:80>
	ServerName example.com
	DocumentRoot /var/www/example.com (không yêu cầu nếu sử dụng Proxy Reverse)
	ErrorLog  Error path log
    	CustomLog  Access path log
</VirtualHost>
- B3: Chạy Certbot cho Apache cho domain tương ứng
sudo certbot --apache
- B4:Sửa conf file SSL do certbot tạo ra thường có tên gần giống ương ứng với tên example.com.ssl.conf
- B5: Config thêm Proxy Reverse cho file config ssl

        <Location "/">
                ProxyPreserveHost On
                ProxyPass http://localhost:8080/
                ProxyPassReverse http://localhost:8080/
        </Location>
- B6: khởi động lại Apache
sudo systemctl restart httpd

Ghi chú:
httpd is the same as apache2. It depends on the OS you use. For example in RHEL 6.2 it is called httpd and in Ubuntu it is called apache2.

- https://www.youtube.com/watch?v=zglf0UWi2gQ
