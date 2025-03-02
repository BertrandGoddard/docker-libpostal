# docker-libpostal

[![CI Build Status](https://travis-ci.org/danger/danger-js.svg?branch=master)](https://travis-ci.org/danger/danger-js)
[![Docker Build Status](https://img.shields.io/docker/build/sleekybadger/libpostal.svg)](https://hub.docker.com/r/sleekybadger/libpostal/)
[![Docker Automated](https://img.shields.io/docker/automated/sleekybadger/libpostal.svg)](https://hub.docker.com/r/sleekybadger/libpostal/)


Base [libpostal](https://github.com/openvenues/libpostal) Docker images built on Alpine Linux.

Versions v1.0.0, v1.1-alpha, v1.1.0 – built on [Alpine Linux](https://alpinelinux.org).

All versions use [sleekybadger/libpostal](https://hub.docker.com/r/docker1811/libpostal) repository,
but each version aligns with the following tags:

* `latest` `1.1-alpine` `1.1.0-alpine`
* `1.1-alpha-alpine`
* `1.0-alpine` `1.0.0-alpine`
* `1.1.0-alpine3.15`
* `1.1.0-alpine3.15-go1.17`
* `1.1.0-alpine3.16`
* `1.1.0-alpine3.16-go1.17`
* `1.1.0-alpine3.16-go1.18`

## Table of Contents

- [Example](#example)
- [License](#license)
- [Credits](#credits)
- [Magic](#magic)

## Example

Using libpostal image to install [pypostal](https://github.com/openvenues/pypostal) package:

```Dockerfile
FROM sleekybadger/libpostal:1.1.0-alpine as libpostal-build

FROM python:3.7.1-alpine

COPY --from=libpostal-build /data /data
COPY --from=libpostal-build /usr/lib/libpostal.so /usr/lib/libpostal.so
COPY --from=libpostal-build /usr/lib/libpostal.so.1 /usr/lib/libpostal.so.1
COPY --from=libpostal-build /usr/include/libpostal /usr/include/libpostal

RUN apk add --no-cache build-base
RUN pip install postal

CMD ["python"]
```

## License

docker-libpostal is released under the [MIT](https://opensource.org/licenses/MIT) license.

## Credits

Thanks to:

* [@mhart](https://github.com/mhart) and his [alpine-node](https://github.com/mhart/alpine-node)
* [@dnephin](https://github.com/dnephin) and his [dobi](https://github.com/dnephin/dobi)

## Magic

(ﾉ◕ヮ◕)ﾉ*:･ﾟ✧
