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