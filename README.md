# Nodered, InfluxDb and Grafana by using docker compose with traefik
Node-Red with InfluxDb and Grafana by using docker compose and traefik2

## Secure Node-Red

By default Node-Red is not secured. If you would like to secure your Node-Red application with username and password you have to enable this in the node-red settings file. You will find this file in:
./nodered-storage/settings.js

Uncommend the settings within "adminAuth":

 adminAuth: {
        type: "credentials",
        users: [{
            username: "admin",
            password: "$2a$08$zZWtXTja0fB1pzD4sHCMyOCMYz2Z6dNbM6tl8sJogENOMcxWV9DN.>
            permissions: "*"
        }]
    }

You can create your own hashed password in linux with the command:

htpasswd -bnBC 8 "" password | tr -d ':\n' | sed 's/$2y/$2a/'

Where 'password' is your own password which you want to use for login.

For more information for secure your node-red or other authentication options go to https://nodered.org/docs/user-guide/runtime/securing-node-red.

## Thanks
Thanks to:
https://github.com/schtritoff/docker-compose-influxdb-grafana-nodered for base implementation
and 
https://github.com/wollomatic/simple-traefik for implementation of traefik.
