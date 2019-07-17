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
