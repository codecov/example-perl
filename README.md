Codecov's Perl Example
======================

| [https://codecov.io][1] | [@codecov][2] | [hello@codecov.io][3] |
| ----------------------- | ------------- | --------------------- |

This repository serves as an **Example** on how to use [Devel::Cover::Report::Codecov][4] for Perl.

## Usage
### ExtUtils::MakeMaker
Try this commands as following if you use ExtUtils::MakeMaker.

```
$ cpanm --quiet --notest --skip-satisfied Devel::Cover Devel::Cover::Report::Codecov
$ perl Build.PL
$ ./Build build
$ cover -test -report codecov
```

### Prove
Try this commands as following if you use `prove` direct.

```
$ cpanm --quiet --notest --skip-satisfied Devel::Cover Devel::Cover::Report::Codecov
$ cover -delete
$ HARNESS_PERL_SWITCHES="-MDevel::Cover=+ignore,^local/|^t/" prove -r t
$ cover -report codecov
```

# [![travis-org](https://avatars2.githubusercontent.com/u/639823?v=2&s=50)](https://travis-ci.org) Travis CI [![Build Status](https://travis-ci.org/pine613/example-perl.svg?branch=master)](https://travis-ci.org/pine613/example-perl)
> Append to your `.travis.yml`

```yml
before_script:
  - cpanm --quiet --notest --skip-satisfied Devel::Cover Devel::Cover::Report::Codecov

script:
  - perl Build.PL
  - ./Build build
  - cover -test

after_success:
  - cover -report codecov
```

> ### Start testing with [Travis](https://travis-ci.org/)


[1]: https://codecov.io/
[2]: https://twitter.com/codecov
[3]: mailto:hello@codecov.io
[4]: https://github.com/codecov/codecov-perl
