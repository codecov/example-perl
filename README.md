# [Codecov](https://codecov.io) Perl example

[![Build Status](https://travis-ci.org/codecov/example-clojure.svg?branch=master)](https://travis-ci.org/codecov/example-clojure)
[![codecov.io](https://codecov.io/github/codecov/example-clojure/coverage.svg?branch=master)](https://codecov.io/github/codecov/example-clojure?branch=master)
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcodecov%2Fexample-perl.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcodecov%2Fexample-perl?ref=badge_shield)

## Guide
### CI Setup

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

#### Travis
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

#### GitHub Action

Add to your `.github/workflows/main.yml` file
```yml
jobs:
  codecov:
    runs-on: ubuntu-latest
    container: perl:latest
    steps:
      - uses: actions/checkout@v2
      - name: Run codecov GitHub Action
        env:
          CODECOV_TOKEN: ${{ secrets.CODECOV_TOKEN }}
        run: |
          cpanm --quiet --notest Module::Build Devel::Cover Devel::Cover::Report::Codecov
          perl Build.PL 
          cover -test -report codecov
```

Note that you need to link your GitHub repo to your codecov first and then add the `CODECOV_TOKEN` as a secret to your GitHub repository.

### Producing Coverage Reports
```
cover -report codecov
```


## Caveats
### Private Repos
Repository tokens are required for (a) all private repos, (b) public repos not using Travis-CI, CircleCI or AppVeyor. Find your repository token at Codecov and provide via appending `-t <your upload token>` to you where you upload reports.

## Links
- [Community Boards](https://community.codecov.io)
- [Support](https://codecov.io/support)
- [Documentation](https://docs.codecov.io)

## License
MIT.

Originally authored by [Jakub Elżbieciak](https://elzbieciak.pl/).


[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fcodecov%2Fexample-perl.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fcodecov%2Fexample-perl?ref=badge_large)
