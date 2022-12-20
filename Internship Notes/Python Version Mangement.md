## Introduction

Install multiple python versions and switch between them easily: 
[https://realpython.com/intro-to-pyenv/](https://realpython.com/intro-to-pyenv/) 

It is able to set local versions (to the application folder) and globally (until other specified)
Python pip follows the global version, unless a virtual environment is created, then all the pip packages will be installed there. 

## Installing new version

```
pyenv install -v 3.7.2
```

## Removing version

```
rm -rf ~/.pyenv/versions/2.7.15
```

or 

```
pyenv uninstall 2.7.15
```

## Checking versions

```
pyenv versions
```

Switching versions 

```
pyenv global 2.7.15
```

## Set directory specific version

```
pyenv local 2.7.15
```

Set shell specific version 

```
pyenv shell 2.7.15
```

## Further Configurations

`pyenv` manages multiple versions of Python itself.
`virtualenv`/`venv` manages virtual environments for a specific Python version.
`pyenv-virtualenv` manages virtual environments for across varying versions of Python.