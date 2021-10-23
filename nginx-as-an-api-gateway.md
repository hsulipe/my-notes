# Nginx as an API Gateway

## Tools
![Nginx](https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![Node](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)

## Objective
The concept of this documentation is to try configuring nginx as an API gateway instead of using other frameworks and packages like express. 
The reason I'm doing this is purely out of curiosity and to learn more about Nginx. I don't even know if this is possible but I supose it is.

## References
[Nginx - Beginner's Guide](https://nginx.org/en/docs/beginners_guide.html)
[Nginx - Deploying Nginx as an API Gateway - Part 1](https://www.nginx.com/blog/deploying-nginx-plus-as-an-api-gateway-part-1/)

## Notes
- When configuring Nginx the most important folder is the `/etc/nginx`. This is where all .conf file will be added.
- When serving static files with nginx add those files to the `/www/data/*` directory. You can reference those files in the `.conf` files using the `root` keyword. 
