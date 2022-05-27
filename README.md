## About
Docker based Jupyter templates for science.

- LSP
- Python Formatter
- PDF Export

Supporting Languages
- Python
- Julia
- R
- Scala


All you need is Docker.

## How to Use

```shell
git clone https://github.com/org/repo
cd repo
cd jupyter_base
docker-compose up
```
This creates the `jupyter_base_notebook:latest` image.

Then, run `docker-compose up` at the directory you want to use.

Then, access the url displayed in your terminal.

For example, if you want to use Python and Scala, `cd spy` and run `docker-compose up`.

If you want to enter the container, run this command below.

```shell
docker-compose exec notebook bash
```

If you want to stop containers, run the command below.
```shell
# stop all containers
docker-compose down

# stop all containers and volumes
docker-compose down --volumes
```

In addition, if you want to reset your environment, find the docker image and remove it.
```shell
docker images
docker rmi <image_name>:<tag>
# e.g. docker rmi jupyter_base_notebook:latest
```
## Note
If you want to run multiple containers at once, change each port number in `docker-compose.yaml`. 

```shell
.
├── README.md
├── all_in_one
│   ├── Dockerfile
│   ├── README.md
│   └── docker-compose.yml
├── jupy # python 3.9 & Julia 1.6
│   ├── Dockerfile
│   ├── README.md
│   ├── Untitled.ipynb
│   └── docker-compose.yml
├── jupyter_base # python 3.9
│   ├── Dockerfile
│   ├── README.md
│   ├── config
│   │   ├── jupyter_lab_config.py
│   │   └── jupyter_server_config.json
│   ├── docker-compose.yml
│   ├── notebook
│   │   └── example.ipynb
│   ├── requirements.txt
│   └── resources
│       └── index_ja.tex.j2
├── pyr # python 3.9 & R 4.1
│   ├── Dockerfile
│   ├── Untitled.ipynb
│   └── docker-compose.yml
└── spy # python 3.9 & Scala 2.13, 2.12.
    ├── Dockerfile
    ├── README.md
    ├── Untitled.ipynb
    ├── config
    │   └── metals-ls.json
    └── docker-compose.yml
```


## Memo

pyenv dependencies

```shell
apt install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

R dependencies

- debian buster guide https://cran.r-project.org/bin/linux/debian/

```shell
apt install libjpeg62-turbo-dev \
  libc6-dev \
  r-base=${R_BASE_VERSION}-* \
  r-base-core=${R_BASE_VERSION}-* \
  r-recommended=${R_BASE_VERSION}-*
```
