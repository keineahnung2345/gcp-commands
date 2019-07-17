# gcp-commands
Google cloud platform commands

## gsutil

### install gsutil
[Official doc](https://cloud.google.com/storage/docs/gsutil_install)
```sh
curl https://sdk.cloud.google.com | bash
exec -l $SHELL
gcloud init
```

### lists credentialed accounts
```sh
gcloud auth list
```

### acquire new user credentials to use for Application Default Credentials
[All attempts to get a Google authentication bearer token failed](https://www.kaggle.com/c/youtube8m/discussion/29915)
```sh
gcloud auth application-default login
```
This solves:
```
W tensorflow/core/platform/cloud/googleauthprovider.cc:160] All attempts to get a Google authentication bearer token failed, returning an empty token. Retrieving token from files failed with "Not found: Could not locate the credentials file.". Retrieving token from GCE failed with "Unavailable: Error executing an HTTP request (HTTP response code 0, error code 6, error message 'Couldn't resolve host 'metadata'')".
```

### allow all users to read <your_bucket>
[Allow Public Read access on a GCS bucket?](https://stackoverflow.com/questions/40232188/allow-public-read-access-on-a-gcs-bucket)
```sh
gsutil acl ch -u AllUsers:R gs://<yourbucket>/**
```
To change recursively:
```sh
gsutil acl -r ch -u AllUsers:R gs://<yourbucket>/**
```

### list a bucket
```sh
gsutil ls gs://<your_bucket>/**
```

### create a new bucket
```sh
gsutil mb gs://<new_bucket>
```

### remove <your_bucket>
```sh
gsutil rb gs://<your_bucket>
```

### show the content of a file
```sh
gsutil cat gs://<your_bucket>/<your_file>
```

### copy a local file to GCP
```sh
gsutil cp <file_name> gs://<your_bucket>
```
