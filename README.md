### Dnmp

Docker 搭建 Nginx + MySQL + 多版本 PHP



### 如何新增站点？

1. 调整 docker-compose.yml 文件

2. ```conf/nginx/site/``` 目录下新增站点的 .conf 文件

   ```conf
   server {
       listen       80;
       # 填写你的域名
       server_name  xxx.test;
   
       #charset koi8-r;
       #access_log  /var/log/nginx/host.access.log  main;
   
   		# 填写代码的位置
       root   /var/www/xxx/public;
       index  index.html index.htm index.php;
   
       location / {
           try_files $uri $uri/ /index.php?$query_string;
       }
   
       #error_page  404              /404.html;
   
       # redirect server error pages to the static page /50x.html
       #
       #error_page   500 502 503 504  /50x.html;
       #location = /50x.html {
       #    root   /usr/share/nginx/html;
       #}
   
       # proxy the PHP scripts to Apache listening on 127.0.0.1:80
       #
       #location ~ \.php$ {
       #    proxy_pass   http://127.0.0.1;
       #}
   
       # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
       #
       location ~ \.php$ {
       		# 填写PHP版本对应的容器名
           fastcgi_pass   php7.0.5:9000;
           fastcgi_index  index.php;
           fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
           include        fastcgi_params;
       }
   
       # deny access to .htaccess files, if Apache's document root
       # concurs with nginx's one
       #
       location ~ /\.ht {
           deny  all;
       }
   }
   ```

   

