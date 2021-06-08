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
