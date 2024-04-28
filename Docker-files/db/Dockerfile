FROM mysql:5.7.25

LABEL "Project"="Vprofile"
LABEL "Author"="Avin"

ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"

COPY db_backup.sql docker-entrypoint-initdb.d/db_backup.sql
