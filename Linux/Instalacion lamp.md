# Instalacion de servidor lamp

### Instalar apache

1. Actualizar cache
`$ sudo apt update && sudo apt upgrade -y`
‎      
2. Instalar apache 2
`$ sudo apt install apache2 -y`
‎      
3. Habilitar el servicio de apache2
`$ sudo systemctl enable apache2.service`

### Instalacion de maria DB
1. Instalar servidor y cliente de mariadb
`$ sudo apt install mariadb-server mariadb-client -y`
‎      ‏‏‎
2. Reiniciar y habilitar el servicio de mariadb
    ```
    $ sudo systemctl restart mariadb.service
    $ sudo systemctl enable mariadb.service
    ```
3. Instalar mariadb en modo seguro
`$ sudo mysql_secure_installation`‏‏‎
    * Enter the current password for root
    * Set root password: y
    * Type the new password
    * Remove anonimous user: y
    * Disallow root login remotely: n
    * Remove test database: y
    * Reload privilege tables now: y
‎      
4. Reiniciar nuevamente el servicio de mariadb
`$ sudo systemctl restart mariadb.service`
‎      ‏‏‎
5. Ingresar a la consola de mariaDB
`$ sudo mysql -u root -p`
‎      ‏‏‎
6. Actualizar plugin de contraseña
    ``` sql
    > UPDATE mysql.user SET  plugin = 'mysql_native_password' 
      WHERE user = 'root' AND plugin = 'unix_socket';

    > FLUSH PRIVILEGES;

    > EXIT;
    ```

El archivo de configuracion esta en la ruta: **/etc/mysql/mariadb.conf.d/50-server.cnf**

### Instalacion de PHP

1. Listar paquetes disponibles
`$sudo apt-cache pkgnames | grep php7.4`
‎      

2. Instalar PHP
`sudo apt-get install php7.4 -y`
‎      
3. Instalar CLI de php y paquetes adicionales
`$ sudo apt-get install php7.4-{cli,bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm} -y`
‎      
4. Comprobar la version de php
`$ php --version`
‎      
5. Reinciar apache
`$ sudo service apache2 restart`

