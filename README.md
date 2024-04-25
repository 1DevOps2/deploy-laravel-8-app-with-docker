# deploy laravel8 app with docker

## create directory
```
mkdir deploy; cd deploy
```

## download deployemnt files into `deploy` directory 
```
wget https://raw.githubusercontent.com/1DevOps2/deploy-laravel-8-app-with-docker/main/startup.sh
wget https://raw.githubusercontent.com/1DevOps2/deploy-laravel-8-app-with-docker/main/default.conf
wget https://raw.githubusercontent.com/1DevOps2/deploy-laravel-8-app-with-docker/main/Dockerfile
```

## clone your project into `deploy` directory
```
git clone github.com/your-repo.git
```
## copy .env file into into `deploy` directory
```
cp proejct/.env .
```

## change in dockerfile
### change project directory name in dockerfile
at line no.6
```
COPY <project-code-directory> /var/www/html/
```

### make sure what coammands you use to run it locally
at line no.22
```
RUN composer update
RUN composer install
#RUN php artisan optimize
RUN php artisan cache:clear
RUN php artisan config:clear
RUN php artisan route:clear
RUN php artisan key:generate
```

## change in startup.sh
if you aren't using seeds then comment the line no.3. 
```
php artisan db:seed
```

## build docker image
```
docker build -t app .
```
## create docker network
```
docker network create mynet
```

## run mariadb container 


