# PHPConf.Asia Server Setup Scripts

## Additional Steps

1. Run `mysql_secure_installation`

2. Create `opencfp` database

3. Prepare Letsencrypt (https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04):

    ```
    sudo certbot --nginx -d cfp.phpconf.asia
    ```