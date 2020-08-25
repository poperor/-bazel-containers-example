# bazel-containers-example

This repo is based on the excellent tutorial [Create Container images with Bazel](https://dev.to/schoren/create-container-images-with-bazel-47am)

The repo is the end result of going through the tutorial.

## Bazel version

Bazel is embedded in the repo via Bazelisk in ./bin. Both a Linux and a Mac version (darwin) is included here. This means that to run the examples in the tutorial one must exchange the bazel command with eiter ./bin/linux/bazelisk or ./bin/darwin/bazelisk

e.g

```
./bin/linux/bazelisk run //:gazelle


./bin/linux/bazelisk build //...

./bin/linux/bazelisk run //cmd/api

./bin/linux/bazelisk run --platforms=@io_bazel_rules_go//go/toolchain:linux_amd64 //cmd/api:image
```

## curl for posting request to the hasher service

```
curl -d '{"plain": "string to hash"}' -H 'Content-Type: application/json' http://localhost:8000/hash

curl -d '{"hashed": "$2a$10$L/qIKVRTX6TlOORmR//XjuH48Qlks4ZaCMlCgqZAee5mXXJrNNTnq", "compare_to": "string to hash"}' -H 'Content-Type: application/json' http://localhost:8000/compare
```

## Docker run to be able to run on port 8000 on localhost

```
docker run --rm -it -p 8000:8000 poperor/cmd/api:image
```
