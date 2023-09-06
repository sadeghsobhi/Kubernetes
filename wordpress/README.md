# [Deploying WordPress and MySQL with Persistent Volumes](https://kubernetes.io/docs/tutorials/stateful-application/mysql-wordpress-persistent-volume/)


#  Add resource configs for MySQL and WordPress
## The following manifest describes a single-instance MySQL Deployment. The MySQL container mounts the PersistentVolume at /var/lib/mysql. The MYSQL_ROOT_PASSWORD environment variable sets the database password from the Secret.

```
kubectl apply -f db-wordpress.yml
```

## Verify that the Secret exists by running the following command:
```
kubectl get secrets
```
## Verify that a PersistentVolume got dynamically provisioned.

```
kubectl get pvc
```
## Verify that the Pod is running by running the following command:

```
kubectl get services wordpress
```

## The following manifest describes a single-instance WordPress Deployment. The WordPress container mounts the PersistentVolume at /var/www/html for website data files. The WORDPRESS_DB_HOST environment variable sets the name of the MySQL Service defined above, and WordPress will access the database by Service. The WORDPRESS_DB_PASSWORD environment variable sets the database password from the Secret kustomize generated.

```
kubectl apply -f dashboard-wordpress.yml
```

## create wordpress ingress file

```
kubectl apply -f ingress-config.yml
```

## Verify that a Ingress object.

```
kubectl get ingress
```

## After defining the domain name, log in through the website and view the service