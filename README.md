# browserstack-alpine-bug

Demonstrates an issue with BrowserstackLocal on alpine linux container

## Run
```
> docker-compose up
```
Outputs the following, showing that the binary doesn't work properly on alpine:
```
...
test-alpine_1  | standard_init_linux.go:178: exec user process caused "no such file or directory"
browserstackalpinebug_test-alpine_1 exited with code 1
test-debian_1  | BrowserStack Local version 6.8
browserstackalpinebug_test-debian_1 exited with code 0
```
