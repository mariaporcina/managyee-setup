FROM mysql:8.0-debian
ENV MYSQL_ALLOW_EMPTY_PASSWORD=True
ENV TS=America/Sao_Paulo
COPY ./db.sql /docker-entrypoint-initdb.d/
