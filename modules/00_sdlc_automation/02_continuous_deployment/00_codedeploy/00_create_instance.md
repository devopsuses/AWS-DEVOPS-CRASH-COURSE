1. Browse to https://bitnami.com/stack/nginx/cloud/aws/amis.
2. Find the region you operate in and click on the link for the latest version of NGINX.
3. In the `Name and Tags` panel name the instance `webserver01`.
4. Add a tag named `tier` and give it the value `web`.
5. In the `Keypair` panel select `default`.
6. Under the `Network Settings` panel select `Allow http trafic from the internet.`
7. Verify the instance has finished booting by browsing to it by ip address.
