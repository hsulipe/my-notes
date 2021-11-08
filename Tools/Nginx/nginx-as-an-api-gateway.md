# Nginx as an API Gateway

## Tools
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![Node](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)

## Objective
The concept of this documentation is to try configuring nginx as an API gateway instead of using other frameworks and packages like express.  

The reason I'm doing this is purely out of curiosity and to learn more about Nginx. I don't even know if this is possible but I supose it is.

## Notes
- When configuring Nginx the most important folder is the `/etc/nginx`. This is where all .conf file will be added.
- When serving static files with nginx add those files to the `/www/data/*` directory. You can reference those files in the `.conf` files using the `root` keyword. 
### Initial steps

At first, I tried coping this [configuration](https://gist.github.com/nginx-gists/37ce65292a06219ff8d35d293c05e0b5#file-api_gateway-conf) just to test and see how it worked. The only modifications that I made, were removing the api_keys.conf file and changing from ssl to http.  

Also I wrote this into the Dockerfile configuration, so I could run this in both my windows or my linux machine.
```
FROM nginx:latest

WORKDIR /etc/nginx

COPY *.conf ./
COPY api_conf.d .

EXPOSE 80
```
After building and runing through the localhost, I could acess the nginx container. But the `localhost/api/warehouse` endpoint was not found. And this is the log I received.
```
2021/10/24 13:06:50 [error] 32#32: *1 open() "/usr/share/nginx/html/api/warehouse" failed (2: No such file or directory), client: 172.17.0.1, server: localhost, request: "GET /api/warehouse HTTP/1.1", host: "localhost"
```
What I'm supossing it happened is that the nginx is searching for an static file in the directory `/usr/share/nginx/html/api/warehouse`. But this is not what I want, I want it to execute some javascript function. Having an similar behavior as an AWS API Gateway and an AWS Lambda function integration.

### Firecracker

After searching more on the web. I discorvered that under the hood AWS Lambda Functions use Firecracker REST-API to create an microVM with the function's CPU and memory settings. [Reference](https://blog.oliverjumpertz.dev/how-aws-lambda-works-under-the-hood). This blog also tells me that I need to create a bootstrap code that will be waiting for requests to execute my handler function.

What I discovered about Firecracker is that it runs on a giant instance and it shares resources between each execution of the lambda functions on microVMs. Firecracker wores about Securety, Isolation, Monitoring and Scalability. But for this project this won't be necessary. So for now we won't go futher on firecracker.


### Docker Compose

I created the following docker-compose file to run the nginx container along side my app container. Then I tried accessing my app server through the nginx exposed web-server. But it was unsuccessful :worried:. The nginx container still trying to open an static file.

```
version: '3.9'
services:
  webserver:
    build: ./gateway/api/
    ports:
      - '80:80'
  app:
    build: .
    ports:
      - '8080:8080'
```

## References
[Nginx - Beginner's Guide](https://nginx.org/en/docs/beginners_guide.html)  
[Nginx - Deploying Nginx as an API Gateway - Part 1](https://www.nginx.com/blog/deploying-nginx-plus-as-an-api-gateway-part-1/)  
[How AWS Lambda Works Under The Hood](https://blog.oliverjumpertz.dev/how-aws-lambda-works-under-the-hood)  
[Firecracker](https://firecracker-microvm.github.io/)  
[How AWS’s Firecracker virtual machines work | Amazon Science](https://www.youtube.com/watch?v=BIRv2FnHJAg)  
[Express under the hood](https://medium.com/man-moon/express-js-under-the-hood-6452c897b316)  