[![nginx 1.17.2](https://img.shields.io/badge/nginx-1.17.2-brightgreen.svg?&logo=nginx&logoColor=white&style=for-the-badge)](https://nginx.org/en/CHANGES) [![php 7.3.8](https://img.shields.io/badge/php--fpm-7.3.8-blue.svg?&logo=php&logoColor=white&style=for-the-badge)](https://secure.php.net/releases/7_3_8.php)


## Introduction
This is a Dockerfile to build a debian based container image running nginx and php-fpm 7.3.x / 7.2.x / 7.1.x / 7.0.x & Composer.

### Versioning
| Docker Tag | GitHub Release | Nginx Version | PHP Version | Debian Version |
|-----|-------|-----|--------|--------|
| latest | master Branch |1.17.2 | 7.3.8 | buster |


## How to use this repository
The build is automatically triggered by a git push to your feature/[branch]

## First clone the repository to your workstation
```
$ git clone https://gitlab.com/propitix/microservices/php-frontend.git
$ cd frontend-propitix
```

Create a feature branch. # Always start with feature/[name of your branch]
```
git branch -b feature/add-css-style-to-about-us-page
```


Update the application code in
```
./html/
```

Then add/commit/push to gitlab

```
git status # to see your changes
```

```
git add --all # If you are satisfied with your changes and willing to push everything. Otherwise, select only the files to add
```

```
git commit -m "Put some message about this push here"
```

## Push your changes to gitlab, and merge to dev branch
```
git push --set-upstream origin feature/[Your branch name]
```

### Validate your changes have been triggered by gitlab-ci in
[propitix-scm] (https://gitlab.com/propitix/microservices/frontend-propitix)

### Check the image have been pushed to
[Google Container Registry] (https://console.cloud.google.com/gcr/images/non-prod-pdz/EU/frontend-propitix?project=non-prod-pdz&authuser=1&gcrImageListsize=30) (Depending on the environment. Either non-prod or prod)

## pulling the image
```
docker pull eu.gcr.io/$environment/frontend-propitix:$tag-version
```

## Running (You can do this step without the pulling the above as it will put down if not found locally)
To run the container:
```
$ docker run -d eu.gcr.io/$environment/frontend-propitix:$tag-version
```

Default web root:
```
/usr/share/nginx/html
```

## If you require permissions to GCP, or Gitlab resources, please talk to dare@propitix.com
