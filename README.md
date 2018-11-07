[![Build Status](https://travis-ci.org/apicollective/apibuilder.svg?branch=master)](https://travis-ci.org/apicollective/apibuilder)

apibuilder
==========

Simple, Comprehensive Tooling for Modern APIs.

See https://www.apibuilder.io


how to run
============


1.install SBT
===
install

    $ brew install sbt@1


Memory settings for SBT:

    exec java -Xms512M -Xmx2048M -XX:MaxPermSize=1G -Xss1M -XX:+CMSClassUnloadingEnabled \ 
      ${SBT_OPTS} -jar /usr/local/Cellar/sbt/0.13.5/libexec/sbt-launch.jar "$@"

2.Database
===

You'll need to run the postgresql database (version 9.5 or greater). Two options:

  1. docker run -d -p 5432:5432 flowcommerce/apibuilder-postgresql:latest

  2. run locally - see the project https://github.com/apicollective/apibuilder-postgresql
     - You need to run `psql -U api apibuilderdb ./setup-test-data.sql` to get the `dev` user


3.start API Service 
===
in console under apibuilder root folder run:
    $ sbt
    sbt> project api
    sbt> run 9001

4.start App 
===

    $ sbt
    sbt> project app
    sbt> run
    
5.start project generator 
===

If you want to run the standard code generators service locally you can clone it from [apibuilder-generator](https://github.com/apicollective/apibuilder-generator)

    $ sbt
    sbt> project generator
    sbt> run 9002

6.configure generator 
===
To configure generators in local api builder instance:

  1. Goto http://localhost:9000/generators
  2. Click 'Add generator'
  3. Enter 'http://localhost:9002' for service URI

Now both should be running and able to talk to each other, and should recompile
in site for a nice development experience.

App Url -[http://localhost:9000](http://localhost:9000/)


