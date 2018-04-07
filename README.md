# PHPConf.Asia Server Setup Scripts

## Additional Steps

1. Run `mysql_secure_installation`

2. Create `opencfp` database

    ```
    CREATE DATABASE opencfp;
    CREATE USER 'opencfp'@'localhost' IDENTIFIED BY '$uperSecureP@ssw0rd';
    GRANT ALL PRIVILEGES ON opencfp.* TO 'opencfp'@'localhost';
    FLUSH PRIVILEGES;
    ```

3. Prepare folder

    ```
    chmod 777 bin/*
    chmod 777 script/*
    script/setup
    ```

4. Prepare Letsencrypt (https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04):

    ```
    sudo certbot --nginx -d cfp.phpconf.asia
    ```

