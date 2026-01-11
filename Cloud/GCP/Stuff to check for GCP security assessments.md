
```bash
gsutil ls gs://bucket_name
```

if this returns output and lists the files in the storage bucket

```bash
gsutil cp -r gs://bucket_name .
```

& , if this downloads the contents of the bucket into the directory named `bucket_name` 

it means that an attacker who doesnt even have to be a user of the service, or have an account, can LIST (read) and GET (Download) the buckets contents. The above commands executing without authentication means that Public LIST and GET access on the bucket is available