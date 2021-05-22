## Раздел в разработке

    - PHP Composer
    - Перенести основные моменты с которыми встречаюсь на пыхе
    - PhpStrom
    - Работа с временными зонами
    - Шпаргалка
    
## Composer
    * Как установить composer
    - https://www.digitalocean.com/community/tutorials/how-to-install-and-use-composer-on-ubuntu-20-04-ru
    
    * Если не настроены права на /var/www/ , можно сделать следующее
    ```
    // Проверка какие группы существуют
    cat /etc/group 
   
    sudo usermod -aG www-data ${USER}
    su - ${USER}
    sudo chown -R mclaren:www-data /var/www/
    sudo chmod 775 /var/www/
    ```
