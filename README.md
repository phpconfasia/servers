# PHPConf.Asia Server Setup Scripts

## Running Ansible Script

1. Rename `ansible/hosts.sample` to `ansible/hosts`

2. Run the Ansible Playbook

    ```
    cd ansible
    ansible-playbook -i ./hosts main.yml
    ```

## Additional Steps

1. Run `mysql_secure_installation`

2. Create `opencfp` database

    ```
    CREATE DATABASE opencfp;
    CREATE USER 'opencfp'@'localhost' IDENTIFIED BY '$uperSecureP@ssw0rd';
    GRANT ALL PRIVILEGES ON opencfp.* TO 'opencfp'@'localhost';
    FLUSH PRIVILEGES;
    ```

3. Prepare folders

    ```
    CFP_ENV=production script/setup
    chmod -R 777 cache
    chmod -R 777 log
    chmod -R 777 web/uploads
    chown -R www-data:www-data cache
    ```

4. Prepare Letsencrypt (https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04):

    ```
    certbot certonly --webroot --agree-tos --no-eff-email --email admin@phpconf.asia -w /var/www/letsencrypt -d cfp.phpconf.asia
    ```

5. Promote user

    ```
    bin/console user:promote --env=production admin@phpconf.asia admin
    ```
