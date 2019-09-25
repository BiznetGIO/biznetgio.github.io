# Project Boilerplates

---

## python-boilerplate

https://github.com/BiznetGIO/python-boilerplate

### Project Structure

This the the flask boilerplate that you can use to to kickstart your next REST API
project. The app structure of this boilerplate is:

``` bash
.
├── app    # application module
│   ├── configs
│   ├── controllers
│   │   └── api
│   ├── helpers
│   ├── libs
│   ├── middlewares
│   ├── models
│   └── static
├── docker-compose.yml # docker compose config
├── Dockerfile   # docker config
├── .dockerignore
├── .env.example # environment variable examples
├── .gitignore
├── README.md
├── requirements.txt  # depedencies
├── run.sh
└── test
```

- `configs`: contains configuration variables. e.g API keys,
  database URIs, or variable of the application instance (things like
  DEBUG=True). You can ignore this if you are using docker environments.

- `controllers/api`: contains "routes" of the application.

- `helpers`: this directory act like "helpers" or "utilitiles" functions the
  applications

- `libs`: this directory act like "vendor", or any third-party module that you
  want to deliver within the application.

- `middlewares`: contains files that related to http request. e.g auth
  files. (you can ignore it at the beginning)

- `models`: contains models of the application.
- `static`: contains your static files .e.g images, javascript files.
- `test`: contains test suites against the application logic
- `run.sh`: contains files that will import the app and start the server.

### Quickstart

To start using this boilerplate:

``` bash
# install required dependencies
$ pip install -r requirements.txt

# run the app
python manage.py server
```
