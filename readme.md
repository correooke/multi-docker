## Desarrollo

Se genera mediante docker-compose up --build
Se utiliza nginx como servidor clave para los archivos estáticos

## Productivo 

### Integración con TravisCI y AWS

Las imágenes son construidas mediante la configuración del archivo .travis.yml y los respectivos Dockerfiles, y luego se hace el push de las imágenes productivo a DockerHub.
De allí las tomará AWS mediante su ECS donde tiene configuradas las tareas (task) y el archivo de configuración Dockerrun.aws.json