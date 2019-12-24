
## subir docker stack

* caso de que se use swarm mode en vez de docker-compose para agregar cpus al contenedor.

```
docker stack deploy --compose-file docker-compose.yml vossibility
```

## instalar magento

docker exec -it <container_name> install-magento


## desactivar cache

* luego de desactivar cache refrescar los modulos

```
php bin/magento cache:disable
```

## refrescar todos los modulos

```
rm -rf var
rm -rf generated/*
php bin/magento setup:upgrade
php bin/magento setup:di:compile

php bin/magento setup:static-content:deploy -f en_GB
# php bin/magento setup:static-content:deploy -f en_US #en el caso que contenido estatico sea en_US
chmod -R 0777 var generated/ pub
```

## mostrar log de debug

```
tail -f var/log/debug.log
```

## mostrar log de system

```
tail -f var/log/system.log
```


## ????

```
php bin/magento maintenance:disable 
```


## crear usuario administrador

```
php bin/magento admin:user:create --admin-user=admin --admin-password=magentorocks1 --admin-email=hi@mageplaza.com --admin-firstname=Mageplaza --admin-lastname=Family
```


## mostrar modo de magento

```
php bin/magento deploy:mode:show
```


## camboar a developer mode

```
rm -rf generated/metadata/* generated/code/*
php bin/magento deploy:mode:set developer
```

## Limpar cache

```
php bin/magento cache:clean
php bin/magento cache:flush
```


Composer
==========


## instalar dependencia en local para usar en magento.

* editar archivo composer.js de magento

```
  "repositories": [
      {
          "type": "path",
          "url": "/var/pago-facil-core"
      }
  ],
```

* usar comando para agregar dependencia local
    * en carpeta raiz de magento.

```
composer require kdu/pagofacilcore
```