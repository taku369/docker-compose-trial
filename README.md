## Reference
https://docs.docker.com/compose/gettingstarted/

### Usage
```bash
$ docker compose up --watch
[+] Running 2/0
 ✔ Container docker-compose-trial-redis-1  Created                                                                                                                    0.0s
 ✔ Container docker-compose-trial-web-1    Created                                                                                                                    0.0s
        ⦿ Watch enabled
Attaching to redis-1, web-1
redis-1  | 1:C 17 Oct 2024 11:41:21.939 * oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
redis-1  | 1:C 17 Oct 2024 11:41:21.939 * Redis version=7.4.1, bits=64, commit=00000000, modified=0, pid=1, just started
redis-1  | 1:C 17 Oct 2024 11:41:21.939 # Warning: no config file specified, using the default config. In order to specify a config file use redis-server /path/to/redis.conf
redis-1  | 1:M 17 Oct 2024 11:41:21.940 * monotonic clock: POSIX clock_gettime
redis-1  | 1:M 17 Oct 2024 11:41:21.942 * Running mode=standalone, port=6379.
redis-1  | 1:M 17 Oct 2024 11:41:21.943 * Server initialized
redis-1  | 1:M 17 Oct 2024 11:41:21.944 * Loading RDB produced by version 7.4.1
redis-1  | 1:M 17 Oct 2024 11:41:21.944 * RDB age 11 seconds
redis-1  | 1:M 17 Oct 2024 11:41:21.944 * RDB memory usage when created 0.95 Mb
redis-1  | 1:M 17 Oct 2024 11:41:21.944 * Done loading RDB, keys loaded: 1, keys expired: 0.
redis-1  | 1:M 17 Oct 2024 11:41:21.945 * DB loaded from disk: 0.002 seconds
redis-1  | 1:M 17 Oct 2024 11:41:21.945 * Ready to accept connections tcp
web-1    |  * Serving Flask app 'app.py'
web-1    |  * Debug mode: on
web-1    | WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
web-1    |  * Running on all addresses (0.0.0.0)
web-1    |  * Running on http://127.0.0.1:5000
web-1    |  * Running on http://172.19.0.3:5000
web-1    | Press CTRL+C to quit
web-1    |  * Restarting with stat
web-1    |  * Debugger is active!
web-1    |  * Debugger PIN: 473-704-675
```

```bash
$ docker image ls
REPOSITORY                    TAG             IMAGE ID       CREATED         SIZE
docker-compose-trial-web      latest          c7433622dcd3   4 minutes ago   224MB
redis                         alpine          e105cfd78d67   13 days ago     41.2MB
```

```bash
$ docker ps -a
CONTAINER ID   IMAGE                      COMMAND                   CREATED         STATUS         PORTS                    NAMES
33b4d306b465   redis:alpine               "docker-entrypoint.s…"   9 seconds ago   Up 9 seconds   6379/tcp                 docker-compose-trial-redis-1
634de97a7113   docker-compose-trial-web   "flask run --debug"       9 seconds ago   Up 9 seconds   0.0.0.0:8000->5000/tcp   docker-compose-trial-web-1
```

```bash
$ docker compose ls
NAME                   STATUS              CONFIG FILES
docker-compose-trial   running(2)          /programming/docker-compose-trial/compose.yaml

$ docker compose ps
NAME                           IMAGE                      COMMAND                   SERVICE   CREATED         STATUS         PORTS
docker-compose-trial-redis-1   redis:alpine               "docker-entrypoint.s…"   redis     2 minutes ago   Up 2 minutes   6379/tcp
docker-compose-trial-web-1     docker-compose-trial-web   "flask run --debug"       web       2 minutes ago   Up 2 minutes   0.0.0.0:8000->5000/tcp
```
