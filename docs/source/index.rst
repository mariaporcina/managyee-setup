Tutorial: rodando aplicação CRUD - Docker + Docker Compose + Dockerfile
===================================

Ambiente
--------

OS: Ubuntu 22.04 LTS (Jammy)

Docker: v26.1.3

Docker Compose: v2.27

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

.. .. toctree::

..    usage
..    api






Passo 1. Download dos arquivos de configuração
-------------------------------------------------

Faça o clone do repositório com os arquivos de configuração do ambiente, em uma pasta de nome “managyee”, com o comando abaixo.

```git clone https://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@github.com/mariaporcina/managyee-setup.git managyee```

Em seguida, acesse a pasta ```managyee/```.

Passo 2. Download dos arquivos da aplicação
-------------------------------------------

Acesse a pasta web/ e faça o clone do repositório com os arquivos da aplicação CRUD, em uma pasta de nome “www”, com o comando abaixo.

```git clone https://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@github.com/mariaporcina/company-management.git www```

Passo 3. Confira a configuração da conexão com o banco de dados
---------------------------------------------------------------

Acesso o arquivo ```managyee/web/www/config.php``` e confira se o server, username, password e name do banco de dados estão corretos. Se necessário, corrija.

Passo 4. Faça uma cópia do arquivo db.sql para a pasta /db
----------------------------------------------------------

Volte para a pasta raiz da configuração (```managyee/```).

Faça uma cópia do arquivo ```managyee/web/www/db.sql``` para dentro da pasta managyee/db utilizando o comando abaixo:

```cp ./web/www/db.sql ./db/db.sql```

Passo 5. Inicie a aplicação
---------------------------

Garanta que está dentro da pasta ```managyee/``` ou uma das suas pastas filhas e utilize o comando abaixo para inicializar a aplicação:

```docker compose up -d```

Caso necessário, para parar a aplicação, utilize o comando:

```docker compose down```

Para remover por completo, inclusive os volumes, utilize:

```docker compose down --rmi all -v```
