Codecov's Perl Example
======================

| [https://codecov.io][1] | [@codecov][2] | [hello@codecov.io][3] |
| ----------------------- | ------------- | --------------------- |

This repository serves as an **Example** on how to use [Devel::Cover::Report::Codecov][4] for Perl.

## Usage
### ExtUtils::MakeMaker
Try this commands as following if you use ExtUtils::MakeMaker.

```
$ cpanm --quiet --notest --skip-satisfied Devel::Cover::Report::Codecov
$ perl Build.PL
$ ./Build build
$ cover -test -report codecov
```

### Prove
Try this commands as following if you use `prove` direct.

```
$ cpanm --quiet --notest --skip-satisfied Devel::Cover::Report::Codecov
$ cover -delete
$ HARNESS_PERL_SWITCHES="-MDevel::Cover=+ignore,^local/|^t/" prove -r t
$ cover -report codecov
```

# [![travis-org](https://avatars2.githubusercontent.com/u/639823?v=2&s=50)](https://travis-ci.org) Travis CI &nbsp;[![Build Status](https://travis-ci.org/codecov/example-perl.svg?branch=master)](https://travis-ci.org/codecov/example-perl)
> Append to your `.travis.yml`

```yml
before_script:
  - cpanm --quiet --notest --skip-satisfied Devel::Cover::Report::Codecov

script:
  - perl Build.PL
  - ./Build build
  - cover -test

after_success:
  - cover -report codecov
```

> ### Start testing with [Travis](https://travis-ci.org/)

# [![codeship](https://avatars1.githubusercontent.com/u/2988541?v=2&s=50)](https://codeship.io/) Codeship
> Append to your `Setup Commands`

```sh
curl -L https://cpanmin.us | perl - App::cpanminus
export PATH=~/perl5/bin:$PATH
cpanm --local-lib=~/perl5 local::lib && eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)
cpanm --quiet --installdeps --notest .
cpanm --quiet --notest --skip-satisfied Devel::Cover::Report::Codecov
```

> Append to your `Test Commands`

```sh
perl Build.PL
./Build build
cover -test -report codecov
```

> Append to your `Environment Variables`

```sh
CODECOV_TOKEN=<YOUR_UPLOAD_TOKEN>
```

> ### Start testing with [Codeship](https://codeship.io/)

# [![circleci](https://avatars0.githubusercontent.com/u/1231870?v=2&s=50)](https://circleci.com/) Circle CI (1.0)
> Append to your `circle.yml` file

```yml
machine:
  environment:
    PATH: ~/perl5/bin:$PATH

dependencies:
  pre:
    - curl -L https://cpanmin.us | perl - App::cpanminus
    - cpanm --local-lib=~/perl5 local::lib && echo "eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)" >> ~/.bashrc
    - cpanm --quiet --notest --skip-satisfied Devel::Cover::Report::Codecov

test:
  override:
    - perl Build.PL
    - ./Build build
    - cover -test

  post:
    - cover -report codecov
```

> Append to your `Environment Variables`

```sh
CODECOV_TOKEN=<YOUR_UPLOAD_TOKEN>
```

> ### Start testing with [Circle CI](https://circleci.com/)

We are happy to help if you have any questions. Please contact email our Support at [support@codecov.io](mailto:support@codecov.io)

[1]: https://codecov.io/
[2]: https://twitter.com/codecov
[3]: mailto:hello@codecov.io
[4]: https://github.com/codecov/codecov-perl
