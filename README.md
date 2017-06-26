# docker-sync
Docker configuration running docker-sync

## Setup Instructions ##

1. Install docker-sync
   - `gem install docker-sync`
2. Clone a docker-sync instance for your project
   - `git clone git@github.com:gabrielqs-redstage/docker-sync.git <your-project-name>`
3. Clone your project repository under ./src
   - `cd src`
   - `git clone <your_project_git_url>`
4. Place a database dump into ./src
5. Edit docker-compose.yml, docker-compose-dev.yml and docker-sync.yml, replacing <project_name> with your project's name.
6. Spin up the docker containers:  
   - `./start`
7. Attach to the phpfpm container:
   - `docker-compose exec phpfpm bash`
8. From the phpfpm container, import the db and set the base_urls:
   - `mysql -hmariadb -umagento -pmagento magento < db.sql`
9. Adjust app/etc/env.php, using this file
10. Create an entry in /etc/hosts pointing to 127.0.0.1
    - `sudo vim /etc/hosts`
11. Open a new browser and open http://<your_domain>/ (nginx is running at port 80)
