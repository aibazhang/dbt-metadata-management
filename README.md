# dbt Metadata Management

An example of metadata management by dbt on BigQuery

## Edit `profiles.yml`

1. replace `{YOUR_DATASET_NAME}`
2. replace `{YOUR_PROJECT_ID}`

## Install with Docker

1. Pull image

```console
docker pull ghcr.io/dbt-labs/dbt-bigquery:1.2.0
```

2. Running a dbt Docker image in a container

bash/zsh

```console
docker run --rm \
  --network=host \
  --platform linux/amd64 \
  --mount type=bind,source=`PWD`,target=/usr/app \
  --mount type=bind,source=`PWD`/profiles.yml,target=/root/.dbt/profiles.yml \
  --mount type=bind,source=$HOME/.config/gcloud/application_default_credentials.json,target=/root/.config/gcloud/application_default_credentials.json \
  ghcr.io/dbt-labs/dbt-bigquery:1.2.0 \
  ls
```

fish

```console
docker run --rm \
  --network=host \
  --platform linux/amd64 \
  --mount type=bind,source=$(PWD),target=/usr/app \
  --mount type=bind,source=$(PWD)/profiles.yml,target=/root/.dbt/profiles.yml \
  --mount type=bind,source=$HOME/.config/gcloud/application_default_credentials.json,target=/root/.config/gcloud/application_default_credentials.json \
  ghcr.io/dbt-labs/dbt-bigquery:1.2.0 \
  ls
```

## Generating Documents

bash/zsh

```console
docker run --rm \
  --network=host \
  --platform linux/amd64 \
  --mount type=bind,source=`PWD`,target=/usr/app \
  --mount type=bind,source=`PWD`/profiles.yml,target=/root/.dbt/profiles.yml \
  --mount type=bind,source=$HOME/.config/gcloud/application_default_credentials.json,target=/root/.config/gcloud/application_default_credentials.json \
  ghcr.io/dbt-labs/dbt-bigquery:1.2.0 \
  docs generate
```

fish

```console
docker run --rm \
  --network=host \
  --platform linux/amd64 \
  --mount type=bind,source=$(PWD),target=/usr/app \
  --mount type=bind,source=$(PWD)/profiles.yml,target=/root/.dbt/profiles.yml \
  --mount type=bind,source=$HOME/.config/gcloud/application_default_credentials.json,target=/root/.config/gcloud/application_default_credentials.json \
  ghcr.io/dbt-labs/dbt-bigquery:1.2.0 \
  docs generate
```

## Generating static html file

```console
python generate_static_html.py
```

Open `target/index2.html` by your browser.

**Done**