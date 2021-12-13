<div align="center">

<img src="https://www.python.org/static/community_logos/python-logo-generic.svg" width="320px" />

# Template Python Project

![Python Version](https://img.shields.io/github/pipenv/locked/python-version/mundoalem/template-python-project)
![Release Version](https://img.shields.io/github/v/release/mundoalem/template-python-project)
![Pipeline Status](https://github.com/mundoalem/template-python-project/actions/workflows/on_tag.yml/badge.svg)
[![codecov](https://codecov.io/gh/mundoalem/template-python-project/branch/main/graph/badge.svg?token=R0HJ0SAOC0)](https://codecov.io/gh/mundoalem/template-python-project)
![Contributors](https://img.shields.io/github/issues/mundoalem/template-python-project)

A DevOps centric template to bootstrap Python projects.

</div>

## Introduction

This project is a template anyone can use in order to bootstrap a project using the Python programming language. The
template has a full featured pipeline following the latest DevOps practices.

You can control the project through the use of [pipenv](https://pipenv.pypa.io/), it accepts the following targets:

| Argument | Description                                           |
| -------- | ----------------------------------------------------- |
| build    | Build source and wheel packages                       |
| clean    | Remove build files and directories                    |
| docs     | Build documentation                                   |
| install  | Install the project inside the virtual environment    |
| lint     | Check the code for syntax issues and style            |
| release  | Release the package to PyPi                           |
| reset    | Removes build files, directories and test environment |
| scan     | Scan the project for security vulnerabilities         |
| test     | Test the project                                      |

## License

[GPLv3](https://choosealicense.com/licenses/gpl-3.0/)

## Tech Stack

These are the software baked in this template:

- [Python 3.9](https://www.python.org/)
- [bandit](https://github.com/PyCQA/bandit)
- [black](https://github.com/psf/black)
- [coverage](https://github.com/nedbat/coveragepy)
- [invoke](http://docs.pyinvoke.org/en/stable/)
- [mypy](http://www.mypy-lang.org/)
- [pytest](https://pypi.org/project/pytest/)
- [Sphinx](https://www.sphinx-doc.org/en/master/)
- [twine](https://twine.readthedocs.io/en/latest/)

## Usage

In order to use this template you first need to clone this repo locally:

```
$ git clone git@github.com:mundoalem/template-python-project.git
$ cd template-python-project/
```

After you finish cloning the template you can start using it right away, however
it may be better to make the project your own by:

- Configure `setup.cfg` file with your project details.
- Configure in `tox.ini` file the `envlist` property with the Python versions you need.
- Add your license to `LICENSE` file.
- Update the license header in all Python files.
- Configure in `.coveragerc` the `source` property of your project (usually the name of the project).
- Update test files under `tests` directory.
- Make sure you are using the correct Python versions in the jobs configured in `.github/workflows`.
- Make sure to remove the `--noop` argument in the `release` step of the pipeline in `.github/workflows/pipeline.yml`.
- Update the `README.md` with your project information.
- Update `settings` section in `.devcontainer/devcontainer.json` with your preferred Visual Studio Code settings.

All pipeline jobs can be also run locally by invoking `pipenv` scripts, example:

```
$ pipenv run build
$ pipenv run lint
$ pipenv run test
$ pipenv run scan
$ pipenv run release
```

## Environment Variables

To run this project, you will need to add the following environment variables to your environment:

| Variable           | Description                                                           |
| ------------------ | --------------------------------------------------------------------- |
| CODECOV_TOKEN      | Token used to calculate and report test coverage from codecov.io      |
| SNYK_TOKEN         | Token used during the security vulnerabilities scan task from snyk.io |
| PYPI_PASSWORD      | PyPi Password used during the release process                         |
| PYPI_USERNAME      | PyPi User Name used during the release process                        |
| PYPI_PASSWORD_TEST | PyPi Test Password used during the release process                    |
| PYPI_USERNAME_TEST | PyPi Test Password used during the release process                    |

## Feedback

If you have any feedback, please open an [issue](https://github.com/mundoalem/template-python-project/issues).

## Contributing

In particular, this community seeks the following types of contributions:

- Participate in an issue thread or start your own.
- Help us ensure that this repository documentation is comprehensive.
- Implement new features to the project.
- Fix open issues.

## Conduct

We are committed to providing a friendly, safe and welcoming environment for all, regardless of gender, sexual
orientation, disability, ethnicity, religion, income or similar personal characteristic.

Please be kind and courteous. There's no need to be mean or rude. Respect that people have differences of opinion and
that every design or implementation choice carries a trade-off and numerous costs. There is seldom a right answer,
merely an optimal answer given a set of values and circumstances.

Please keep unstructured critique to a minimum. If you have solid ideas you want to experiment with, make a fork and see
how it works.

We will exclude you from interaction if you insult, demean or harass anyone. That is not welcome behavior. We interpret
the term "harassment" as including the definition in the [Citizen Code of Conduct](http://citizencodeofconduct.org/);
if you have any lack of clarity about what might be included in that concept, please read their definition. In
particular, we don't tolerate behavior that excludes people in socially marginalized groups.

Whether you're a regular contributor or a newcomer, we care about making this community a safe place for you and we've
got your back.

Likewise any spamming, trolling, flaming, baiting or other attention-stealing behavior is not welcome.

## Communication

GitHub issues are the primary way for communicating about specific proposed changes to this project.

In both contexts, please follow the conduct guidelines above. Language issues are often contentious and we'd like to
keep discussion brief, civil and focused on what we're actually doing, not wandering off into too much imaginary stuff.

## FAQ

### Will there ever be support for other continuous integration platforms?

Right now I have no plans to support other platforms like TravisCI, CircleCI or Gitlab. Anyway, it should be quite
easy for you to port the GitHub Actions to any platform you like.

The reason for that is that I don't want to have a `.travis.yml`, a `circleci.yml` and a `.gitlab-ci.yml` all together
in the same place when only one would actually be used. So I want to avoid (for now) cluttering the template with too
many files that might or might not be useful.

### Why did you drop support for multiple Python versions?

The main reason why I dropped support for multiple versions in the project is because it is quite hard to define a set
of project standards since it is not clear which version should be the main one. For example, when we create the
virtual environment which version should we use? What should we do if one of our dependencies work in different ways
across versions? What version should we pick for the IDE? Pipenv should be installed for all versions or just the
default system one? When should we drop support for a version?

As you can see there are lots of questions that are hard to find an answer for in a generic way, since most people
using the template will have their own preferences and it is likely, in this case, that whatever option we choose will
make most users unhappy.

Therefore, the philosophy of the project is to aim on using a stable version that is supported by all development
packages. For example, version `3.10` is out but yet not fully adopted by tools like `pipenv` and `black`, so we are
still using the `3.9` version until `3.10` is widely supported.

If you need to support multiple versions, for example `3.7`, ` 3.8` and `3.9` my recommendation is to locally develop
in the lowest one (`3.7`) and configure the `test` step in the pipeline to run on all three.

### I don't like Visual Studio Code! Are you going to support other text editors?

That's also a difficult topic since text editors and IDE's all work in different ways and support different features.
The reason for Visual Studio Code (vscode) is because it is free, open source, widely adopted by the community,
supports remote development and enables me to have all the editor configuration as code.

Other development environments like `PyCharm` might be better in some aspects, but there is little room to customize
their workflow and you can't share it in an easy way.

As a DevOps engineer you are always trying to improve agility by creating automation that facilitates other people's
workflows. Unfortunately, it's easy to face frustration and resistance as most people get used to their tools and their
own ways of doing things.

Having said that, you can still make use of the template for other text editors and IDE's but you will need to find out
on your own how to integrate the features of this template to those tools.
