https://stackoverflow.com/a/52007971
https://github.com/sagardere/set-up-SSL-in-nodejs
- https://github.com/sindresorhus/guides/blob/main/run-node-server-alongside-apache.md


*Môi trường linux
[Yêu cầu cài certbot
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

- https://www.youtube.com/watch?v=zglf0UWi2gQ](https://stackoverflow.com/a/52007971 https://github.com/sagardere/set-up-SSL-in-nodejs
* https://github.com/sindresorhus/guides/blob/main/run-node-server-alongside-apache.md


*Môi trường linux Yêu cầu cài certbot Yêu cầu cài apache
* B1: truy cập theo đường dẫn /etc/httpd/conf.d
* B2: tạo file conf Vd: example.com.conf
* B2: Tạo VirtualHost tương ứng VD <VirtualHost *:80> ServerName example.com DocumentRoot /var/www/example.com (không yêu cầu nếu sử dụng Proxy Reverse) ErrorLog Error path log CustomLog Access path log
* 
<IfModule mod_ssl.c>
<VirtualHost *:443>
        ServerAdmin carebox.vantaidvt.com.vn
        ServerName carebox.vantaidvt.com.vn
        ProxyPreserveHost On
        ProxyPass / http://127.0.0.1:3470/
        ProxyPassReverse / http://127.0.0.1:3470/


SSLCertificateFile /etc/letsencrypt/live/carebox.vantaidvt.com.vn/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/carebox.vantaidvt.com.vn/privkey.pem
Include /etc/letsencrypt/options-ssl-apache.conf
</VirtualHost>
</IfModule>

- B3: Chạy Certbot cho Apache cho domain tương ứng: sudo certbot --apache -d dogoxuanthu.com
- B4:Sửa (hoặc không sửa) conf file SSL do certbot tạo ra thường có tên gần giống ương ứng với tên example.com.ssl.conf - - B5: Config thêm Proxy Reverse cho file config ssl

<VirtualHost *:80>
        ServerAdmin carebox.vantaidvt.com.vn
        ServerName carebox.vantaidvt.com.vn
        ProxyPreserveHost On
        ProxyPass / http://127.0.0.1:3470/
        ProxyPassReverse / http://127.0.0.1:3470/
RewriteEngine on
RewriteCond %{SERVER_NAME} =carebox.vantaidvt.com.vn
RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]
</VirtualHost>

* B6: khởi động lại Apache sudo systemctl restart httpd
* 
Ghi chú: httpd is the same as apache2. It depends on the OS you use. For example in RHEL 6.2 it is called httpd and in Ubuntu it is called apache2.
* https://www.youtube.com/watch?v=zglf0UWi2gQ

sudo certbot -apache -d your_domain -d www.your_domain

sudo certbot --apache -d mvd.hopto.org

Đề nghị NNT lưu lại mã xác nhận này (Mã này dùng để mở lại thông tin tờ khai lưu tạm): f3994a)
