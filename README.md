# Personal template for Laravel

## Requirements
- Docker

## What's included
- Reduced Sail Laravel 9. (only mysql and mailhog containers)
- Laravel livewire
- Breeze auth & tailwind & alpinejs starter kit
- Larastan (static code analysis)
- Github CI setup for auto deployment with a webhook (host agnostic)

## Setup & use
### Local setup
```shell
cp .env.example .env
```
```shell
composer install
```
```shell
sail up -d
```
```shell
sail artisan key:generate
```
```shell
sail artisan migrate
```
```shell
sail npm i
```

### Local use when developing
Start sail
```shell
sail up -d
```
And run vite in dev mode
```shell
sail npm run dev
```

### Github CI setup
The following setup is for a staging environment, you can adapt it by modifying `.github/workflows` files too.
- Go to the "Settings" tab of your repo, then go to "Secret and variables" > "Actions".
- Add new repository secret, name it `STAGING_WEBHOOK_SECRET` and put a personalized token. It should be the same that your env variable `WEBHOOK_SECRET` in `.env` file
- Add another secret, name it `STAGING_WEBHOOK_URL` and put your website url with https scheme, and without trailing slash (ex: `https://example.com`)   

Then, you should authorize github actions to push to your repo :
- Go to the "Settings" tab of your repo, then go to "Actions" > "General".
- Check "Read and write permissions" at "Workflow permissions" section
