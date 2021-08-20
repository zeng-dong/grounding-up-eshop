# setup the project
1. right click Services and Add Solution Foler: Basket
2. right click solution and Add New Project
3. choose ASP.NET Core Web Api
4. name: Basket, location: append physical location (src\Services\Baskeet) after default: (default is: C:\Dev\githubrepos\GroundingUpEShop).

# redis
1. docker pull redis
2. docker run -d -p 6379:6379 --name aspnetrun-redis redis
3. docker logs -f aspnetrun-redis
4. [docker exec -it aspnetrun-redis /bin/bash] to get into the container and ready to run redis commands
5. redis cli:
	5.1. [rdis-cli] and the prompt changes to '127.0.0.1:6379>'
	5.2  set key zd
	5.3  get key
	5.4  set name my
	5.5  get name


# containerize
1. right click Basket.API and add Container Orchestrator Support ...
2. select Docker Compose
3. select Linux
4. OK
5. a Dockerfile is generated under the project, and docker-compose that already exists got modified
6. modify docker-compose to config basketdb
7. now run 'docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d' and I can see:
/c/dev/githubrepos/GroundingUpEShop/src (main)
$ docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d
Creating network "src_default" with the default driver
Creating basketdb  ... done
Creating catalogdb ... done
Creating catalog.api ... done
Creating basket.api  ... done

and I can access http://localhost:8001/swagger/index.html and http://localhost:8000/swagger/index.html

# container management with Portainer
- resources:
	* https://hub.docker.com/r/portainer/portainer-ce
	* https://documentation.portainer.io/archive/1.23.2/deployment/
- intro
	manage container-based software application
- add to our docker-compose
	1. add service into docker-compose
	2. add 'portainer_data:' to volumes
	3. modify docker-compose.override to have 'portainer' service
- run it: docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d
	* docker ps
	* localhost:9000
	* admin/admin1234
