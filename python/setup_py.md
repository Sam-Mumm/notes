# setup.py

## Beispiel
```
from setuptools import setup, find_packages

setup(
    name = 'wiki',
    version = '1.0.0',
    url = 'https://github.com/Sam-Mumm/wiki.git',
    author = 'Dan',
    author_email = 'author@gmail.com',
    description = 'Description of my package',
    packages = find_packages(),
    install_requires = ['flask', 'matplotlib >= 1.5.1'],
)
```