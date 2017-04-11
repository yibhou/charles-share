Charles Proxy Firefox SSL Fix
Jan 2015

This is a fix for latest version of Firefox which doesn't accept Charles SSL cert as it's before 1970. You should really generate your own certs but here's mine if you're lazy.

Password for everything is charles.

Import .pem into Firefox, Firefox settings > Advanced > Certificates > View Certificates > Import
Import .p12 into Charles, Proxy > Proxy Settings > SSL > Use a custom CA certificate

Restart Charles and it should work. Any problems, post to the superuser.com thread.

http://superuser.com/questions/864886/get-firefox-to-trust-expired-charles-ca-certificate