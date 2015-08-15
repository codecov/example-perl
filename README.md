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

# [![codeship](https://avatars1.githubusercontent.com/u/2988541?v=2&s=50)](https://codeship.io/) Codeship [ ![Codeship Status for pine613/example-perl](https://codeship.com/projects/40a2d330-2560-0133-f5b1-72f090cba113/status?branch=master)](https://codeship.com/projects/96951)
> Append to your `Setup Commands`

```sh
curl -L https://cpanmin.us | perl - App::cpanminus
export PATH=~/perl5/bin:$PATH
cpanm --local-lib=~/perl5 local::lib && eval $(perl -I ~/perl5/lib/perl5/ -Mlocal::lib)
cpanm --quiet --installdeps --notest .
cpanm --quiet --notest --skip-satisfied Devel::Cover Devel::Cover::Report::Codecov
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


[1]: https://codecov.io/
[2]: https://twitter.com/codecov
[3]: mailto:hello@codecov.io
[4]: https://github.com/codecov/codecov-perl
