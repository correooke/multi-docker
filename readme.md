## Desarrollo

Se genera mediante docker-compose up --build
Se utiliza nginx como servidor clave para los archivos estáticos

## Productivo 

### Integración con TravisCI y AWS

Las imágenes son construidas mediante la configuración del archivo .travis.yml y los respectivos Dockerfiles, y luego se hace el push de las imágenes productivo a DockerHub.
De allí las tomará AWS mediante su ECS donde tiene configuradas las tareas (task) y el archivo de configuración Dockerrun.aws.json

## Configuración AWS 

Region: us-east-1

MainVPC                 | MainVPC-Subnet
vpc-0f3853408ae960c08   |

Security Group: multi-docker => my-multi-docker (sg-02b6bd0bacb191d50)
****Custom TCP Rule TCP 5432 - 6379

### EB

Aplication Name: multi-docker => multi-docker-2
Entorno de ejecución: MultiDocker-env => MultiDocker-env-2

### DB

multi-docker-postgres
- Master Username: postgres
- Pass: postgres
- Databasename: fibvalues
- vpc-postgres:  vpc-e3c9739b

### Redis (ElastiCache)

multi-docker-redis
multi-docker-redis-vpc
- vpc-redis: vpc-0f3853408ae960c08
- security group: my-multi-docker (sg-02b6bd0bacb191d50)
- subnet-056db1a4724a1302b us-east-1c
- subnet-050560858fa9c0935 us-east-1b

Creo una imagen desde:
 - ImageFromEB


### AWS User

multi-docker-deployer
AWS_ACCESS_KEY: id clave de acceso: <>
clave de acceso secreta: <>



