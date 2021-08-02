# docker-protoc
protoc packaged in docker


# Usage
* bash
  ```bash
  docker run --rm -it -v `pwd`:/your-project-name -w /your-project-name AsynkronIT/protoc:latest -I=. --gogoslick_out=. shared/*.proto
  docker run --rm -it -v `pwd`:/your-project-name -w /your-project-name AsynkronIT/protoc:latest -I=. --gograinv2_out=. shared/*.proto
  ```
* Makefile
  ```Makefile
  root_dir:=$(CURDIR)
  protoc:=docker run --rm -it \
  	-v $(root_dir):/your-project-name \
  	-w /your-project-name \
  	AsynkronIT/protoc:latest

  proto:
  	$(protoc) -I=.  --gogoslick_out=. shared/*.proto
  	$(protoc) -I=.  --gograinv2_out=. shared/*.proto
  ```

# Build
```
docker build -t yourname:latest .
```
or if you want use `GOPROXY`
```
docker build -t yourname:latest --build-arg protoc_version=3.17.3 --build-arg=goproxy=https://goproxy.io,direct .
```
That's all.
