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
```
