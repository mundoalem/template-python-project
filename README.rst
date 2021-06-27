Python Project Template
-----------------------

A template to scaffold a Python project.

You can control the project through pipenv scripts ``scripts/project.sh``, you can
pass it the following arguments:

.. list-table:: 
  :header-rows: 1

  * - Argument
    - Description
  * - build
    - Build source and wheel packages
  * - clean
    - Remove build files and directories
  * - docs
    - Build documentation
  * - install
    - Install the project inside the virtual environment
  * - lint
    - Check the code for syntax issues and style
  * - release
    - Release the package to PyPi
  * - reset
    - Removes build files, directories and test environment
  * - scan
    - Scan the project for security vulnerabilities
  * - test
    - Test the project
  * - test37
    - Test the project
  * - test38
    - Test the project
  * - test39
    - Test the project
   

License
-------

`GPLv3 <https://choosealicense.com/licenses/gpl-3.0/>`_


Tech Stack
----------

These are the software baked in this template:

* Python 3.7, 3.8 and 3.9
* black
* coverage
* invoke
* mypy
* pytest
* Sphinx
* tox
* twine


Usage
-----

In order to use this template you first need to clone this repo locally:

.. code-block:: bash

  git clone git@github.com:mundoalem/template-python-project.git


Example:

.. code-block:: bash
  
  $ pipenv run build
  $ pipenv run lint
  $ pipenv run test
  $ pipenv run scan
  $ pipenv run release


Environment Variables
---------------------

To run this project, you will need to add the following environment variables to your .env file

.. list-table:: 
  :header-rows: 1

  * - Variable
    - Description
  * - ``SNYK_TOKEN``
    - Token used during the security vulnerabilities scan task from Snyk.io
  * - ``PYPI_PASSWORD``
    - PyPi Password used during the release process
  * - ``PYPI_USERNAME``
    - PyPi User Name used during the release process
  * - ``PYPI_PASSWORD_TEST``
    - PyPi Test Password used during the release process
  * - ``PYPI_USERNAME_TEST``
    - PyPi Test Password used during the release process


Feedback
--------

If you have any feedback, please reach out to us at info@mundoalem.io

  
Contributing
------------

Contributions are always welcome!


FAQ
---

Question 1

Answer 1
