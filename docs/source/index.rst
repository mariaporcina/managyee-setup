Configurando Aplicação CRUD Conteinerizada + DNS
================================================

Documentação da aplicação Managyee.

CRUD desenvolvido com PHP e MySql.

Ambiente
========

Ambiente conteinerizado com Docker, utilizando as ferramentas Docker Compose com Dockerfile.

OS: Ubuntu 22.04 LTS (Jammy)

Docker: v26.1.3

Docker Compose: v2.27

DNS
===

Para a configuração do DNS foi utilizado a ferramenta bind9.

Os seguintes arquivos foram editados:

- named.conf.options
- named.conf.local
- db.managyee.com

Passo 1. Configurar named.conf.options
--------------------------------------

Definir IP's que deverão ser disponibilizados para acesso:

>>> dnssec-validation no;
>>> allow-query { <inserir IP de onde o app está hospedado>; 127.0.0.0/8; };

Não é necessário habilitar ipv6:

>>> listen-on-v6 { };

Passo 2. Configurar named.conf.local
------------------------------------

Definir a zona:

>>> zone "managyee.com" IN {
>>>	type master;
>>>	file "db.managyee.com";
>>> };

Passo 3. Configurar db.managyee.com

Configurar registros do domínio:

>>> $ORIGIN managyee.com.
>>> $TTL 300;
>>> @ IN SOA dns maria.porcina.mp.gmail.com (1 30 30 30 30);
>>> @ IN NS dns
>>> @ IN A <inserir IP de onde o app está hospedado>
>>> web IN CNAME @
>>> www IN CNAME @
>>> db IN A <inserir IP de onde o banco de dados está hospedado>
>>> traefik IN A <inserir IP de onde a ferramenta está hospedada>
>>> dns IN A <inserir IP de onde o DNS está configurado>

Tutorial: rodando aplicação CRUD - Docker + Docker Compose + Dockerfile
=======================================================================



.. **Lumache** (/lu'make/) is a Python library for cooks and food lovers
.. that creates recipes mixing random ingredients.
.. It pulls data from the `Open Food Facts database <https://world.openfoodfacts.org/>`_
.. and offers a *simple* and *intuitive* API.

.. Check out the :doc:`usage` section for further information, including
.. how to :ref:`installation` the project.

.. .. note::

..    This project is under active development.

.. Contents
.. --------

.. toctree::

   usage
   api






Passo 1. Download dos arquivos de configuração
----------------------------------------------

Faça o clone do repositório com os arquivos de configuração do ambiente, em uma pasta de nome “managyee”, com o comando abaixo.

>>> git clone https://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@github.com/mariaporcina/managyee-setup.git managyee

Em seguida, acesse a pasta ``managyee/``.

Passo 2. Download dos arquivos da aplicação
-------------------------------------------

Acesse a pasta web/ e faça o clone do repositório com os arquivos da aplicação CRUD, em uma pasta de nome “www”, com o comando abaixo.

>>> git clone https://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@github.com/mariaporcina/company-management.git www

Passo 3. Confira a configuração da conexão com o banco de dados
---------------------------------------------------------------

Acesso o arquivo ``managyee/web/www/config.php`` e confira se o server, username, password e name do banco de dados estão corretos. Se necessário, corrija.

Passo 4. Faça uma cópia do arquivo db.sql para a pasta /db
----------------------------------------------------------

Volte para a pasta raiz da configuração (``managyee/``).

Faça uma cópia do arquivo ``managyee/web/www/db.sql`` para dentro da pasta managyee/db utilizando o comando abaixo:

>>> cp ./web/www/db.sql ./db/db.sql

Passo 5. Inicie a aplicação
---------------------------

Garanta que está dentro da pasta ``managyee/`` ou uma das suas pastas filhas e utilize o comando abaixo para inicializar a aplicação:

>>> docker compose up -d

Caso necessário, para parar a aplicação, utilize o comando:

>>> docker compose down

Para remover por completo, inclusive os volumes, utilize:

>>> docker compose down --rmi all -v
