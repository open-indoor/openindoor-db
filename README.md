# openindoor-db

## Local development
### reset all
```
$ docker-compose rm
```
### Start the db and db adminer

```
$ docker-compose up openindoor-db openindoor-adminer
```
### Import data
```
$ docker-compose up openindoor-gdal
```

### Check the result
```
$ docker-compose up openindoor-tegola
```

## Deployment on k8s
### Kubectl secret management
```kubectl create secret generic <secret_store_name> --from-literal=<secret_var1_name>='<secret_var1_value' --from-literal=<secret_var2_name>='<secret_var2_value>'```

After this it can be used in kubernetes .yaml file by secret store name:
```
  envFrom:
    - secretRef:
        name: <secret_store_name>
```
