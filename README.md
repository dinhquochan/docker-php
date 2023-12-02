# Docker PHP-FPM & Nginx base on Alpine Linux

Simple docker image for PHP/Laravel development. This is a folk from [pnlinh/docker-php](https://github.com/pnlinh/docker-php).

### Why should use this image

- Built on the lightweight and
  secure [Alpine Linux](https://www.alpinelinux.org/) distribution
- Multi-platform, supporting AMD4, ARMv6, ARMv7, ARM64
- Use [runit](http://smarden.org/runit/) instead
  of [supervisor](http://supervisord.org/)
- Very small Docker image size

### PHP version support

- [x] PHP 8.0
- [x] PHP 8.1 (recommend usage)
- [x] PHP 8.2 (recommend usage)
- [x] PHP 8.3

### How to use

- Build image

```shell
VERSION=8.0 make build # Build image with php 8.0
VERSION=8.1 make build # Build image with php 8.1
VERSION=8.2 make build # Build image with php 8.2
VERSION=8.3 make build # Build image with php 8.3
```

- How to customize image name

```shell
VERSION=7.2 IMAGE=archielite/laravel:php make build # Build image with php 7.2
VERSION=7.4 IMAGE=archielite/laravel:php make build # Build image with php 7.4
VERSION=8.0 IMAGE=archielite/laravel:php make build # Build image with php 8.0
VERSION=8.1 IMAGE=archielite/laravel:php make build # Build image with php 8.1
VERSION=8.2 IMAGE=archielite/laravel:php make build # Build image with php 8.2
VERSION=8.3 IMAGE=archielite/laravel:php make build # Build image with php 8.3
```

- Test image by PHP version

```shell
VERSION=8.3 make test
VERSION=8.2 make test
VERSION=8.1 make test
VERSION=8.0 make test
VERSION=7.4 make test
VERSION=7.2 make test
```

- Test all image

```shell
make test-all
```

- Mount your code to be served with container

```shell
docker run --name=app -v /path/to/project:/var/www/html -p 80:80 dinhquochan/laravel:php8.1
```

- Using docker-compose

```
version: '3.4'

services:
    app:
        image: dinhquochan/laravel:php8.1
        hostname: laravel-app
        container_name: laravel-app
        ports:
            - "80:80"
        volumes:
            - .:/var/www/html
        networks:
            - localnet
networks:
    localnet:
        driver: "bridge"
```

- Browser to: [http://localhost](http://localhost)

![image](https://user-images.githubusercontent.com/26193890/198828634-fc11aaa1-7175-4433-b4f3-755381669e74.png)

### Add Xdebug

- See [docs/xdebug-support.md](docs/xdebug-support.md)

### References

- https://github.com/pnlinh/docker-php
- https://github.com/TrafeX/docker-php-nginx
- https://bolshov.online/docker/2020/11/18/runit-vs-supervisor
- https://stackoverflow.com/questions/67231714/how-to-add-trusted-root-ca-to-docker-alpine/67232164#67232164

### Security

If you discover any security related issues, please email contact@dinhquochan.com instead of using the issue tracker.

## Credits

- [Dinh Quoc Han](https://github.com/dinhquochan)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
