# Dokploy deployment

Use `docker-compose.dokploy.yml` as the Compose Path in Dokploy.

## Required environment variables

```env
POSTIZ_HOST=post.andreevmaster.com
JWT_SECRET=replace-with-a-long-random-value
POSTIZ_DB_PASSWORD=replace-with-a-long-random-value
```

Optional variables:

```env
POSTIZ_VERSION=v2.21.8
POSTIZ_DB_USER=postiz
POSTIZ_DB_NAME=postiz
TEMPORAL_DB_PASSWORD=replace-with-a-long-random-value
DISABLE_REGISTRATION=false
```

Configure the Dokploy domain for service `postiz`, container port `5000`, and HTTPS.
Do not expose PostgreSQL, Redis, Elasticsearch, or Temporal publicly.

Add social-provider credentials in Dokploy environment variables. Do not commit
credentials or a production `.env` file to Git.

## Updating Postiz

1. Check the Postiz release notes.
2. Change `POSTIZ_VERSION` in Dokploy to the desired release tag.
3. Redeploy the Compose application.
4. Confirm that `postiz`, PostgreSQL, Redis, and Temporal are healthy.

The application image is pulled from GHCR. Dokploy does not build the Postiz
source tree, so deployments remain fast and upstream source updates do not
create merge conflicts with this Compose file.
