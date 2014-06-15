Cloudfoundry Buildpack: Dancer
==============================

This is an experimental [Cloudfoundry buildpack](http://docs.run.pivotal.io/buildpacks/) for [Dancer](http://www.perldancer.org/).

## Overview

There are three files that comprise a buildpack:

1. `bin/detect` - Determines if this buildpack should be applied to an application.
2. `bin/compile` - Builds the runtime to be leveraged by an application.
3. `bin/release` - Sets up the environment an startup command for an application.

The "heavy lifting" is done by the `bin/compile` script. This particular buildpack is used as the basis of a demo for the [Saint Louis Cloud Foundry Meetup](http://www.meetup.com/Saint-Louis-Cloud-Foundry-Meetup/). Because of that, there are three copies of the `bin/compile` script. This allows us to illustrate a few different ways to approach the preparation of a runtime for Perl developers:

1. `compile.prebuilt` - Illustrates downloading a previously compiled version of Perl to run an application.
2. `compile.source` - Illustrates downloading Perl and compiling it from source.
3. `compile.system` - Illustrates using the system Perl (if available) or using apt-get to install it.

## Usage
```
$ git clone https://github.com/danielkennedy/hello-dancer.git
$ cd hello-dancer/
$ cf push APP_NAME -b https://github.com/danielkennedy/cloudfoundry-buildpack-dancer.git
```
