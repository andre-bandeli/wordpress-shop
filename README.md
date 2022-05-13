# wordpress-shop
![WordPress](https://img.shields.io/badge/WordPress-%23117AC9.svg?style=for-the-badge&logo=WordPress&logoColor=white) ![PHP](https://img.shields.io/badge/php-%23777BB4.svg?style=for-the-badge&logo=php&logoColor=white) ![MySQL](https://img.shields.io/badge/mysql-%2300f.svg?style=for-the-badge&logo=mysql&logoColor=white) ![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)


Repositório criado para testar o ambiente de desenvolvimento do Wordpress + Docker e, posteriormente, deploy de uma loja virtual, utilizando temas/templates livres e gratuitos. 

## Instalação

- Realizar o download das imagens do Wordpress e mySQL no site do docker hub (necessário já ter o docker e o docker compose instalados na máquina)
  - Wordpress:  https://hub.docker.com/_/wordpress
  - mySQL: https://hub.docker.com/_/mysql 

- Criar uma pasta para o projeto (mkdir wp) e nela criar o arquivo docker-compose.yml, que será onde conterá a estrutura necessária para a criação da imagem docker.

  <b>docker-compose.yaml</b>:

        version: '3.1'

        services:

          db:
            image: mysql
            command: --default-authentication-plugin=mysql_native_password
            restart: always
            environment:
              MYSQL_ROOT_PASSWORD: example

          adminer:
            image: adminer
            restart: always
            ports:
              - 8080:8080

        Wordpress docker-compose:
        services:

            wordpress:
               image: wordpress
               restart: always
                ports:
                   - 8080:80
                environment:
              WORDPRESS_DB_HOST: db
              WORDPRESS_DB_USER: exampleuser
              WORDPRESS_DB_PASSWORD: examplepass
              WORDPRESS_DB_NAME: exampledb
          volumes:
              - wordpress:/var/www/html
