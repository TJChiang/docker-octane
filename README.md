# Dockerized Octane image

The base image for [Laravel Octane](https://laravel.com/docs/11.x/octane) with [OpenSwoole](https://pecl.php.net/package/openswoole) extension.

## Pull image and run container!

Pull image

```bash
docker pull ghcr.io/104lab/octane:8.3
```

Run container example:

```bash
docker run --rm -it -v $(pwd):/source -w /source -p 8000:8000 ghcr.io/104lab/octane:8.0 php artisan octane:start
```

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
