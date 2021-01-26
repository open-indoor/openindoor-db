# openindoor-db

## Kubectl secret management
```kubectl create secret generic <secret_store_name> --from-literal=<secret_var1_name>='<secret_var1_value' --from-literal=<secret_var2_name>='<secret_var2_value>'```

After this it can be used in kubernetes .yaml file by secret store name:
```
  envFrom:
    - secretRef:
        name: <secret_store_name>
```
