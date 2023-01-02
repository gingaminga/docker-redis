# Docker with Redis

Docker compose를 사용한 Redis 실행

## 준비하기

```bash
$ git clone https://github.com/gingaminga/docker-redis.git
$ cd docker-redis
```

### .env

**.env.sample** 파일은 사용하는 환경변수들에 대한 설명이 작성되어 있습니다.
참고하여 **.env** 파일을 만듭니다.

```bash
$ vi .env
```

### redis.conf

redis.conf 파일은 Redis의 초기 설정 파일입니다. (v6.2.6 기준)
.env 파일의 `REDIS_DEFAULT_CONFIG_FILE` 에 설정해둔 **경로**와 **파일명**에 맞도록 이동시킵니다. (파일 마운트를 위해 해당 방식을 사용합니다.)

> 💡 **bind 설정**
> redis.conf 파일 내부에 보안과 관련된 `bind` 속성이 있습니다.
> 해당 값을 0.0.0.0 으로 변경해야 docker로 정상 연결이 가능합니다.
> 출처 : [Connecting to Redis running in Docker Container from Host machine](https://stackoverflow.com/questions/41371402/connecting-to-redis-running-in-docker-container-from-host-machine)

## 실행하기

전부 완료됐다면 실행만 하면 됩니다!

```bash
$ docker compose up -d
```

## 확인하기

### Docker 프로세스 확인하기

```bash
$ docker ps
```

![image](https://user-images.githubusercontent.com/60294629/210197647-378198c4-60d4-49f8-82f9-a05b02fff25e.png)

---

### DB 접속 확인하기

[p3x redis ui](https://github.com/patrikx3/redis-ui)를 사용해 접속 테스트했습니다.
![image](https://user-images.githubusercontent.com/60294629/210198839-0bda4cab-ac0e-4073-9b78-48decd2a54b9.png)
