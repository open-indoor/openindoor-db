# openindoor-db

## Local development
### reset all
```
$ docker-compose rm
```
### Start the db and db adminer
![Adminer](doc/adminer.png?raw=true "Adminer")

```
$ docker-compose up openindoor-db openindoor-adminer
```
### Import data
Main command:
```
ogr2ogr -f "PostgreSQL" \
  PG:"dbname='openindoor-db' host='openindoor-db' port='5432' user='openindoor-db-admin' password='admin123'" \
  /data/france/ FranceRoissyEnFranceAroportDeParisCharlesDeGaulle.geojson \
  -nln buildings \
  -overwrite \
  -skipfailures
```
With docker-compose:
```
$ docker-compose up openindoor-gdal
```

### Check the result

![tegola](doc/tegola.png?raw=true "tegola")
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
