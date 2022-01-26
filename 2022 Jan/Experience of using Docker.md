# Experience of using Docker

Created: January 26, 2022
Created by: Anonymous
Tags: Software Tool

# What is Docker?

- One of Container Runtime software tools. It executes and monitors containers.

# Why we use?

- There are lots of benefits while using containers.
    - Lightweight
    - Isolation
    - Portability
- Dockerfile = record of managing multiple servers, Docker image = fixed server status
- In terms of TDD, we can make safe server images successfully with many trials and errors.
- Easily switches port numbers or other environment properties by environment paths.

# Practical Case

## Dockfile

```jsx
FROM openjdk:11
LABEL description="Online Auction Platform, Sago"
EXPOSE 8080
COPY ./build/libs/sago-0.0.1-SNAPSHOT.jar /opt/sago-in-image.jar
WORKDIR /opt
ENTRYPOINT [ "java", "-jar", "sago-in-image.jar" ]
```

## Docker Command

```jsx
docker build -t sago-test-img
```

<img width="567" alt="Screen_Shot_2022-01-26_at_8 56 01_PM" src="https://user-images.githubusercontent.com/15176192/151260364-da6547d0-6a45-4452-8701-5ce2ab35f308.png">

```jsx
docker run sago-test-img
```

<img width="945" alt="Screen_Shot_2022-01-26_at_9 00 31_PM" src="https://user-images.githubusercontent.com/15176192/151260525-53ea2ae6-8e78-429f-a4ee-c6fe02d26e1a.png">

> ❗If you want to connect database server using localhost(e.g. mysql), you should set the url as `host.docker.internal:3306` on behalf of localhost:3306. See [https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach/24326540#24326540](https://stackoverflow.com/questions/24319662/from-inside-of-a-docker-container-how-do-i-connect-to-the-localhost-of-the-mach/24326540#24326540) page.
> 

# Reference

[https://github.com/f-lab-edu/sago](https://github.com/f-lab-edu/sago)

[왜 굳이 도커(컨테이너)를 써야 하나요? - 컨테이너를 사용해야 하는 이유](https://www.44bits.io/ko/post/why-should-i-use-docker-container)
