MAKEFILE_DIR:=$(dir $(abspath $(lastword $(MAKEFILE_LIST))))

default: check

mypy:
	find {{ cookiecutter.project_root_pkg }} -type f -name '*.py' | xargs mypy
	mypy main.py
	find tests -type f -name '*.py' | xargs mypy

isort:
	isort {{ cookiecutter.project_root_pkg }}
	isort main.py
	isort tests

isort-check:
	isort {{ cookiecutter.project_root_pkg }} --check
	isort main.py
	isort tests --check

black:
	black {{ cookiecutter.project_root_pkg }}
	black main.py
	black tests

black-check:
	black --check {{ cookiecutter.project_root_pkg }}
	black --check main.py
	black --check tests

flake8:
	flake8 {{ cookiecutter.project_root_pkg }}
	flake8 main.py
	flake8 tests

format: isort black flake8

check: mypy isort-check black-check flake8

run:
	python3 main.py

test:
	python3 -m unittest discover

clean:

.PHONY: clean mypy isort isort-check black black-check flake8 format check
