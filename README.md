
duckdb-s3-table-buckets


![output](https://github.com/user-attachments/assets/23d18863-c674-4dfd-a32b-464bfaccbd9e)



# Code 
```
export AWS_ACCESS_KEY_ID="XX"
export AWS_SECRET_ACCESS_KEY="XXX"

duckdb  /Users/sshah/IdeaProjects/iceberg-templates/default.duckdb

INSTALL aws;
LOAD aws;
INSTALL httpfs;
LOAD httpfs;
INSTALL iceberg;
LOAD iceberg;
CALL load_aws_credentials();

ash-5.2# aws s3tables get-table --table-bucket-arn arn:aws:s3tables:us-east-1:867098943567:bucket/iceberg-awsmanaged-tables --namespace example_namespace --name silver_orders

{
    "name": "silver_orders",
    "type": "customer",
    "tableARN": "arn:aws:s3tables:<region>:<account_id>:bucket/iceberg-awsmanaged-tables/table/<table_id>",
    "namespace": [
        "example_namespace"
    ],
    "versionToken": "<version_token>",
    "metadataLocation": "s3://<bucket_name>/<table_name>/metadata/<metadata_file>.json",
    "warehouseLocation": "s3://<bucket_name>/<table_name>",
    "createdAt": "2024-12-19T14:11:53.912948+00:00",
    "createdBy": "<account_id>",
    "modifiedAt": "2024-12-19T14:12:02.866786+00:00",
    "ownerAccountId": "<account_id>",
    "format": "ICEBERG"
}



SELECT * FROM iceberg_scan("s3://3XXXX.metadata.json");
```
