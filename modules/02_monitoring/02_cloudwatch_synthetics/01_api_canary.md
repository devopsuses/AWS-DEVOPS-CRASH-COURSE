# API Canary

API Canaries monitor apis by invoking them.

1. From the `Synthetics Canaries` console click `Create canary`.
2. Select `API canary`.
3. Enter `yelb-api` for the name.
4. Click `Add http request`.
5. For the URL enter the dns name of the load balancer folowed by `/api/getstats`.
6. Add additional steps for `/api/hostname`, `/api/getvotes/`