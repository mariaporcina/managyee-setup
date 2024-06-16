Configurações
=============

DNS
===

Para uma navegação mais amigável, também é interessante configurar um DNS (domain name server) para a aplicação.

Nesse projeto em específico, foi utilizado a ferramenta **bind9** para fazer essa configuração, mas também pode ser feito de outras formas.

Para a configuração básicas do bind9 é necessário editar os seguintes arquivos:

- named.conf.options
- named.conf.local

E também criar um arquivo para o registro do domínio e dos subdomínios. Que poderia, por exemplo, ser nomeado:

- db.managyee.com

Credenciais
===========

Banco de dados
--------------

Para que a aplicação funcione corretament, as credenciais do banco de dados precisam ser configuradas.

Isso deve ser feito no arquivo ``mangyee/web/www/config.php``.