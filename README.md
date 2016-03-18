pg-non-persistent
=========================

Build a non persistent docker image containing PostgreSQL latest versions. This may be particularly useful when you need to commit a running docker with attached data. Check tags and releases to see what versions are available.

This image is based on the official PostgreSQL dockerfile, with the only difference that there aren't any volumes defined. You can read documentation from this repository to get a better understanding on how this image can be run:

* https://github.com/docker-library/postgres

This Docker is aimed at tests and development, not for production purposes.


Build and/or run the container
------------------------------

You can build this dockerfile directly from github or pull it directly from the Docker Hub:

```
docker build -t labgeo/pg-non-persistent:9.5  https://github.com/labgeo/postgresql-non-persistent.git#9.5
```

Then, run the image:

```
docker run -p 5433:5432  --name siosedb -e POSTGRES_PASSWORD=postgres -d labgeo/pg-non-persistent:9.5
```

Finally, test if postgresql is running with psql:

```
PGPASSWORD=postgres psql -h localhost -p 5433 -U postgres -d postgres
```