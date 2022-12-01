## nginx 

docker run -d --name web -p 8080:80 nginx

## mysql

docker run \
--detach \
--name=data \
--env="MYSQL_ROOT_PASSWORD=strongpassword123*" \
--publish 3336:3306 \
mysql

## haproxy

apt-get install haproxy -y 

ile yüklemek yaptıktan sonra

/etc/haproxy/haproxy.cfg dosyasına aşağıdaki satırı eklememiz yeterli.

````
frontend proxy
  bind *:<LISTEN PORT>
  mode tcp
  option tcplog
  default_backend server
   
backend server
    mode tcp
    option tcplog
    option tcp-check
    server host <TARGET-IP:TARGET-PORT>
    ````

daha sonra haproxy servisini yeniden başlatabiliriz.
