
# Exportation of configuration

Whenever you want to export the configuration of your alrady configured keycloak instance you can go throught these steps

- navigate to the folder `/opt/keycloak/bin` of the instance running keycloak. for this youcan use 
	- docker exec -it [container id] /bin/bash or
	- In docker desktop -> containers -> [container running keycloak] -> Exec tab
- Run the export command
```sh
./kc.sh export --file [export file]
```
Example:
```sh
./kc.sh export --realm JWM-realm --file /tmp/keycloak-backup-config.json
```
`./kc.sh export --help` for more details

- Back on your host machine find a way to backup that generated file. For example with the `docker cp` command
```sh
docker cp [container id]:[file location in the container] [file location in the host machine]
```
Example:
```sh
docker cp 4234sdfs2:/tmp/keycloak-backup-config.json ./keycloak-backup-config.json
```


# Import configuration

To import a configuration file one can run the followin command from the container :
```sh
/kc.[sh|bat] import --file <file>
```

or mount a volume containing the configuration file and start the container with the command:

```sh
./kc.[sh|bat] start --import-realm
```

For more information visit:
- [The Official documentation](https://www.keycloak.org/server/importExport)
- [This Youtube playlist](https://www.youtube.com/watch?v=1u8GlfKyB_Q&t=366s) or [This one too](https://www.youtube.com/watch?v=G6h3eVNZFg8&list=PLQZfys2xO5kgpa9-qpJly78d-t7_Fnjec&index=4)
