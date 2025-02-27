# PHP, Apache, phpMyAdmin

A Docker Compose-based development environment with PHP 8.2, Apache (with HTTPS), phpMyAdmin, and Composer. This setup serves as a robust alternative to LAMP, XAMPP, and other stacks, ensuring full compatibility with Magento 2.

## Create Certificates

To create self-signed SSL certificates for local development, run the following command:

```bash
cd certificates
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout localhost.key -out localhost.crt -subj "/CN=localhost" 
```


