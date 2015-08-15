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

[1]: https://codecov.io/
[2]: https://twitter.com/codecov
[3]: mailto:hello@codecov.io
[4]: https://github.com/codecov/codecov-perl
