The bucket is used to demo static hosting using `wp-content/uploads/*` stuff from Hookuaaina's 2024-01 exports and/or scrapes (we probably don't need everything from the actual export).

Created the bucket `static.aonalu.net` in the `hownalu` project, following the naming convention at https://cloud.google.com/storage/docs/hosting-static-website-http. (Corresponds to a CNAME `static` that points to `c.storage.googleapis.com`.)

Figured on using the `hownalu` project (see [[hownalu GCP project]]) since it's mainly for experimenting, and if it's used for real then it should only be temporary. Also, the `Aonalu` project (see [[Aonalu GCP project]]) had billing (explicitly) disabled to ensure that it couldn't incur fees from Firebase Hosting.


https://console.cloud.google.com/storage/create-bucket?project=hownalu

https://cloud.google.com/storage/docs/gsutil/commands/web

https://cloud.google.com/storage/docs/hosting-static-website (SSL, requires load balancer)
https://cloud.google.com/storage/docs/hosting-static-website-http

https://www.geeksforgeeks.org/hosting-a-static-website-on-google-cloud-storage-step-by-step-tutorial/
https://medium.com/google-cloud/hosting-a-static-website-on-google-cloud-using-google-cloud-storage-ddebcdcc8d5b
