[![Build Status](https://secure.travis-ci.org/cnelsonsic/SimpleMMO.png?branch=master)](http://travis-ci.org/cnelsonsic/SimpleMMO)

Quick Installation
==================
You will need pip to install the requirements, you can do something like:

    sudo apt-get install python-setuptools python-dev build-essential
or

    sudo yum install python-setuptools python-devel gcc

followed by

    sudo easy_install -U pip

You'll need to use pip to install the required python packages:
    sudo pip install -r requirements.txt

SimpleMMO uses supervisor to control its server processes, so you will need to
start them by running `supervisord` while in the SimpleMMO checkout directory.
You can use `supervisorctl` to check up on the server processes.

Alternately, you can deploy without supervisord (not recommended) and manage
processes yourself.


Databases
=========
SimpleMMO uses a combination of databases to do its job most effectively.

The bulk of database work is done in an SQL database, you can use MySQL, Postgres,
or even SQLite. Basically anything that Elixir (and by extension, SQLAlchemy) supports.

Zones are a little different. They use MongoDB for their data storage needs.
It's fast, but less fault tolerant than the SQL databases.
Keep in mind that when starting for the first time, it may generate a "prealloc"
file that is quite large, on the order of a few gigabytes. For most people,
this will not be a problem. However on storage-limited systems, this may prove
frustrating.

The real problem here is that there is a flag for mongod, --noprealloc, which
should work for its journal files as well, but does not. See the bug at:
https://jira.mongodb.org/browse/SERVER-2733 for more information.

