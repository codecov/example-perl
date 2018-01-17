# [Codecov][1] Perl example

[![Build Status](https://travis-ci.org/codecov/example-clojure.svg?branch=master)](https://travis-ci.org/codecov/example-clojure)
[![codecov.io](https://codecov.io/github/codecov/example-clojure/coverage.svg?branch=master)](https://codecov.io/github/codecov/example-clojure?branch=master)

## Guide
### Travis Setup
Add to your `.travis.yml` file.
```yml
language: perl

before_script:
  - cpanm --quiet --notest --skip-satisfied Devel::Cover::Report::Codecov

script:
  - perl Build.PL
  - ./Build build
  - cover -test

after_success:
  - cover -report codecov
```
### Producing Coverage Reports
```
cover -report codecov
```
### Other CI services
#### [![codeship](https://avatars1.githubusercontent.com/u/2988541?v=2&s=50)](https://codeship.io/) Codeship
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

#### [![circleci](https://avatars0.githubusercontent.com/u/1231870?v=2&s=50)](https://circleci.com/) Circle CI (1.0)
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

## Caveats
### Private Repos
```sh
CODECOV_TOKEN=<YOUR_UPLOAD_TOKEN>
```
## Support

### Contact
- Intercom (in-app messanger)
- Email: [support@codecov.io](mailto:support@codecov.io)
- Slack: [slack.codecov.io](https://slack.codecov.io)
- [gh/codecov/support](https://github.com/codecov/support)

1. More documentation at https://docs.codecov.io
2. Configure codecov through the `codecov.yml`  https://docs.codecov.io/docs/codecov-yaml

## License

MIT.

Originally authored by [Jakub Elżbieciak](https://elzbieciak.pl/).

[1]: https://codecov.io/
