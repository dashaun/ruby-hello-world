# Hello World

## Build

```
$ pack build test-ruby-app --path ./ --buildpack dashaun/ruby-buildpack
cflinuxfs3: Pulling from cloudfoundry/cnb
Digest: sha256:b574d2b6d991b7992cc4a5aca1776dbf836049f08e926dd960341ce9ac5ebd45
Status: Image is up to date for cloudfoundry/cnb:cflinuxfs3
full-cnb-cf: Pulling from paketo-buildpacks/run
Digest: sha256:84f7b60192e69036cb363b2fc7d9834cff69dcbcf7aaf8c058d986fdee6941c3
Status: Image is up to date for gcr.io/paketo-buildpacks/run:full-cnb-cf
latest: Pulling from dashaun/ruby-buildpack
Digest: sha256:7ac4cc72e13437bfd0cfffe3882d43d546e44a4468b1380a583d366844b60378
Status: Image is up to date for dashaun/ruby-buildpack:latest
===> DETECTING
[detector] com.examples.buildpacks.ruby 0.0.1
===> ANALYZING
[analyzer] Restoring metadata for "com.examples.buildpacks.ruby:bundler" from app image
[analyzer] Restoring metadata for "com.examples.buildpacks.ruby:ruby" from app image
===> RESTORING
[restorer] Restoring data for "com.examples.buildpacks.ruby:bundler" from cache
===> BUILDING
[builder] ---> Ruby Buildpack
[builder] ---> Downloading and extracting Ruby 2.5.0
[builder] ---> Installing bundler
[builder] Successfully installed bundler-2.1.4
[builder] 1 gem installed
[builder] ---> Installing gems
[builder] mkdir: cannot create directory '/layers/com.examples.buildpacks.ruby/bundler': File exists
[builder] [DEPRECATED] The `--path` flag is deprecated because it relies on being remembered across bundler invocations, which bundler will no longer do in future versions. Instead please use `bundle config set path '/layers/com.examples.buildpacks.ruby/bundler'`, and stop using this flag
[builder] [DEPRECATED] The --binstubs option will be removed in favor of `bundle binstubs`
[builder] Fetching gem metadata from https://rubygems.org/.........
[builder] Using bundler 2.1.4
[builder] Using mustermann 1.0.3
[builder] Fetching rack 2.0.8
[builder] Installing rack 2.0.8
[builder] Fetching rack-protection 2.0.8
[builder] Installing rack-protection 2.0.8
[builder] Using tilt 2.0.9
[builder] Using sinatra 2.0.7
[builder] Bundle complete! 1 Gemfile dependency, 6 gems now installed.
[builder] Bundled gems are installed into `/layers/com.examples.buildpacks.ruby/bundler`
===> EXPORTING
[exporter] Reusing layer 'launcher'
[exporter] Adding layer 'com.examples.buildpacks.ruby:bundler'
[exporter] Reusing layer 'com.examples.buildpacks.ruby:ruby'
[exporter] Adding 1/1 app layer(s)
[exporter] Reusing layer 'config'
[exporter] *** Images (a7923c13d896):
[exporter]       index.docker.io/library/test-ruby-app:latest
[exporter] Adding cache layer 'com.examples.buildpacks.ruby:bundler'
Successfully built image test-ruby-app
$
```

## Run

```
$ docker run --rm -p 8080:8080 test-ruby-app
[2020-04-30 06:01:22] INFO  WEBrick 1.4.2
[2020-04-30 06:01:22] INFO  ruby 2.5.0 (2017-12-25) [x86_64-linux]
== Sinatra (v2.0.7) has taken the stage on 8080 for development with backup from WEBrick
[2020-04-30 06:01:22] INFO  WEBrick::HTTPServer#start: pid=1 port=8080
```

