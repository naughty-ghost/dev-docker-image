FROM postgres:15

# PostGIS 3.4 for PostgreSQL 15
# https://trac.osgeo.org/postgis/wiki/UsersWikiPostGIS3UbuntuPGSQLApt
RUN apt update && apt install -y \
    ca-certificates \
    gnupg \
    lsb-release \
    curl && \
    curl https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/apt.postgresql.org.gpg >/dev/null &&\
    sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list' && \
    apt update && apt upgrade -y && \
    apt install -y postgresql-15-postgis-3 && \
    apt-get clean
