## API with STRAPI

---

## Docker

> Pull the latest images

```
docker-compose pull
```

```bash
# run to
docker-compose up

# open in navigator
┌─────────────────────────────┐
│ http://localhost:1337/admin │
└─────────────────────────────┘
```

To update the strapi image:

```bash
# run to
sudo chown -R username:username .

# open the package.json file and modify the versions ex: `3.6.2` to `3.6.3` and then
yarn install

yarn build
```

Every time you change something in the frontend by adding some change to the UI, it is necessary to run

```bash
yarn build --clean
```

Link dump default: [data.zip](https://github.com/React-Avancado/landing-page-api/blob/master/data.zip)

## To inject data into the database:

> HOST, DATABASE_USERNAME, DATABASE_NAME = variables are in the database.js file

```bash
# psql -h HOST -U DATABASE_USERNAME -d DATABASE_NAME -W < file.sql
psql -h 127.0.0.1 -U strapi -d strapi -W < strapi.sql

# local
yarn develop
# or docker
yarn build
```

## Dump:

```bash
# -c --if-exists [clean, check if the database already has the tables, if it has everything if it exists]
# --exclude-table=strapi_administrator [in order not to lose the administrator data, it is necessary to delete the specific table]
# -h HOST
# -U DATABASE_USERNAME
# -d DATABASE_NAME
# -W [requesting the password]

cd app

# local
pg_dump -c --if-exists --exclude-table=strapi_administrator -h 127.0.0.1 -U strapi -d strapi -W > strapi_new.sql
# or docker
docker ps
docker exec <container_name> pg_dump -U strapi > strapi_new.sql
```

## Playground with Graphql:

```bash
┌───────────────────────────────┐
│ http://localhost:1337/graphql │
└───────────────────────────────┘
```

## Deploy with Heroku

[Documentation](https://strapi.io/documentation/developer-docs/latest/setup-deployment-guides/deployment/hosting-guides/heroku.html#_7-heroku-database-set-up) | [WSL](https://dev.to/wrightdotclick/heroku-cli-on-wsl-26fp)

> To change heroku directory by subfolder

```bash
# git subtree push --prefix /path heroku <branch>

heroku login
git subtree push --prefix app heroku main
git push heroku main
```

> Set default language in Heroku

```bash
heroku buildpacks:set heroku/nodejs
```
