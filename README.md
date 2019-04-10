# flacon

[![Build Status](https://travis-ci.org/iksaif/flacon.svg?branch=master)](https://travis-ci.org/iksaif/flacon)
[![Coverage Status](https://coveralls.io/repos/github/iksaif/flacon/badge.svg)](https://coveralls.io/github/iksaif/flacon?branch=master)
[![PyPI version](https://badge.fury.io/py/flacon.svg)](https://badge.fury.io/py/flacon)
[![Supported Python versions](https://img.shields.io/pypi/pyversions/flacon.svg)](https://pypi.python.org/pypi/flacon/)

Flask(-Twisted/Gunicorn) microframework for microservices with Prometheus and Sentry support.

The goal is to remove most of the boilerplate necessary to start a simple HTTP application.
This provides:

* Sane arguments (`--host`, `--port`, `--debug`, `--log-level`)
* Support to have a production ready uwsgi container (`--twisted` or `--gunicorn`)
* Prometheus support with default metrics (`flacon.metrics`: See [prometheus_flask_exporter](https://github.com/rycus86/prometheus_flask_exporter))
* Optional sentry support if the `SENTRY_DSN` env var is set.
* If you have a 'static' directory in your module, just put a favicon.ico inside!

## Installation

```bash
pip install flacon

# To use a production ready wsgi server install one of the following extra requirements
pip install flacon[twisted]
pip install flacon[gunicorn]
```

## Quick-start

```python
from flacon import Flacon

flacon = Flacon(__name__)
app = flacon.app  # This is a flask.Flask() app.

@app.route('/example')
def index():
    return 'Example'

def main():
    flacon.run()

if __name__ == '__main__':
    main()
```

Want to know more? Look at [example/app.py](example/app.py), you can run it with `flacon-example`.
