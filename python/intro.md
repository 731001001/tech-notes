# Intro python

[Python main site](https://www.python.org/)

[Python Documentation](https://docs.python.org/3/)

## How to install python to ubuntu server:
```bash
sudo apt-get install python3
```

## How to install pip:
```bash
sudo apt-get install python3-pip
```

## virtualenv

### How to install virtualenv:
```bash
pip install virtualenv
```

### How to create virtualenv:
```bash
virtualenv myenv
```

### How to activate virtualenv:
```bash
source myenv/bin/activate
```

### How to deactivate virtualenv:
```bash
deactivate
```

## Install packages

### How to install python packages:
```bash
pip install package_name
```

### How to install python package from wheel:
```bash
pip install package_name.whl
```

### How to install python package from source:
```bash
pip install .
```

## Build package

## How to build deb package:
```bash
python3 setup.py --command-packages=stdeb.command bdist_deb
```

## How to install deb package:
```bash
sudo dpkg -i package_name.deb
```

## How to build python package:
```bash
python setup.py sdist bdist_wheel
```

