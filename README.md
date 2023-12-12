# Installation

* Install python3
* Install pip
* Access to project directory (if exists)
* Enable and active the virtual environment
```console
$ python3 -m venv .env
$ source ./.env/bin/active
```

* Install python requirement packages
```console
$ pip install -r requirements.txt
```

# Mkdocs

* Init `docs` strucsture
```console
$ mkdocs new .
```

* Run locally
```console
$ mkdocs serve
INFO    -  Building documentation...
INFO    -  Cleaning site directory
INFO    -  Documentation built in 0.03 seconds
INFO    -  [09:40:55] Watching paths for changes: 'docs', 'mkdocs.yml'
INFO    -  [09:40:55] Serving on http://127.0.0.1:8000/
INFO    -  [09:41:05] Browser connected: http://localhost:8000/
```
