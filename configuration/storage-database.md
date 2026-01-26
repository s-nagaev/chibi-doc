---
title: 'Storage & Database'
description: 'Configure persistence layers: Local, Redis, DynamoDB, and InfluxDB.'
---
Chibi supports multiple storage backends for persisting user data and conversation history.

## Storage Priority

Chibi selects the storage backend based on the available configuration, in the following order of priority:

1.  **Redis** (if `REDIS` URL is set)
2.  **DynamoDB** (if `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` are set)
3.  **Local Filesystem** (Default fallback)

## Local Filesystem

The default storage method. Data is serialized using **Python Pickle (`.pkl`)** and stored in the specified directory.

> [!NOTE]
> Since data is stored in binary `.pkl` files, it is not manually editable.

| Variable          | Description                                                                                                  | Default     |
|:------------------|:-------------------------------------------------------------------------------------------------------------|:------------|
| `LOCAL_DATA_PATH` | The absolute path to the directory where Chibi will store its data files. Ensure this directory is writable. | `/app/data` |

## Redis

Redis is the recommended backend for Docker deployments. It offers better performance and handles concurrency well.

| Variable         | Description                                                                                  | Default |
|:-----------------|:---------------------------------------------------------------------------------------------|:--------|
| `REDIS`          | The connection URL for your Redis instance (e.g., `redis://username:password@host:port/db`). | `None`  |
| `REDIS_PASSWORD` | The password for your Redis instance (optional if included in the URL).                      | `None`  |

## AWS DynamoDB

For serverless and high-scale deployments, DynamoDB is supported.

> [!WARNING]
> **Security Advisory**
> Your `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` grant access to your AWS account. Use IAM roles with least privilege.

| Variable                | Description                                       | Default |
|:------------------------|:--------------------------------------------------|:--------|
| `AWS_REGION`            | The AWS region (e.g., `us-east-1`).               | `None`  |
| `AWS_ACCESS_KEY_ID`     | Your AWS access key.                              | `None`  |
| `AWS_SECRET_ACCESS_KEY` | Your AWS secret access key.                       | `None`  |
| `DDB_USERS_TABLE`       | The DynamoDB table name for user data.            | `None`  |
| `DDB_MESSAGES_TABLE`    | The DynamoDB table name for conversation history. | `None`  |

## Metrics (InfluxDB)

Chibi can export operational metrics (e.g., token usage, response times) to InfluxDB.

| Variable          | Description                        | Default |
|:------------------|:-----------------------------------|:--------|
| `INFLUXDB_URL`    | The URL of your InfluxDB instance. | `None`  |
| `INFLUXDB_TOKEN`  | The authentication token.          | `None`  |
| `INFLUXDB_ORG`    | The organization name.             | `None`  |
| `INFLUXDB_BUCKET` | The bucket name for metrics.       | `None`  |
