
Description
===========
Djenesis begets django projects.

Djenesis is a tool that helps with starting and working on Django projects. Virtualenv is a de facto requirement for any python project and especially so with django projects.

Djenesis does require virtualenv, and your first step is installation for your platform.



Virtualenv Installation
=======================

Mac OS X
--------

Windows
-------

Ubuntu
------

Tips & Tricks
-------------

Pip Download Cache
~~~~~~~~~~~~~~~~~~

set the environment variable PIP_DOWNLOAD_CACHE, to reduce the need to download pip packages multiple times.
e.g.

    export PIP_DOWNLOAD_CACHE=~/.pip_download_cache





User Stories
============

I want to create a new default django project
---------------------------------------------
The simplest story, give djenesis a project name and it will initialze a new project.

    $ djenesis djangoproject

This will create a new virtualenv environment at ``./env-djangoproject``, install the latest version of Django, and initialize a new django project at ``./djangoproject`` using the standard django-admin startproject command.


I want to create a new django project based on my custom template
-----------------------------------------------------------------
Probably the most common use case, start a new project based on a preferred project layout

    $ djenesis mynewproject git+https://github.com/concentricsky/djenesis-template.git

this will inflate a new project based on the template found at the git+url in a directory named ``mynewproject`` 
This will also create a virtualenv named ``env-mynewproject`` and install any packages found in requirements.txt found at the toplevel directory in the template.



I want to start working on an existing django project
-----------------------------------------------------
A convienent way to start working on a project.

    $ djenesis -i projectname git+git@github.com:user/project.git

this will initialize a virtualenv ``env-projectname`` and clone the project into ``projectname``, just like without -i but will preserve .git or any other SCM management files. (.hg, .git, .svn) 




I like using mkvirtualenv and workon
------------------------------------
The virtualenvwrapper package is popular and is a convienent way to maintain a lot of different projects.

    $ djenesis -w thenewproject 



Template URL Formats
====================
You can specify a template as either a path to a local file, a URL to a remote .zip or .tgz file, or as a SCM url:: 

  /path/to/local/directory
  http://example.com/django-template.zip
  git+git@github.com:user/project
  git+ssh://user@example.com:port/repository.git#branch
  hg+https://bitbucket.org/user/project
  svn+http://project.googlecode.com/svn/trunk/project




Environment Variables
=====================

**DJENESIS_DEFUALT_TEMPLATE**
  If set, djenesis will use this as the template argument if none is given on the commandline.

**DJENESIS_VIRTUALENVWRAPPER**
  If set to "1", djenesis will default to using the ``mkvirtualenv`` and ``workon`` commands.

**DJENESIS_VIRTUALENVWRAPPER_PATH**
  The path to where virtualenvwrapper.sh has been installed.


Usage
=========

::

    Usage: djenesis [options] <project_name> [template]
    Options:
      -h, --help            show this help message and exit
      -e VIRTUALENV, --virtualenv=VIRTUALENV
                            Specify the path to create the virtualenv
      -i, --initialize      Initialize from an existing project (dont remove scm
                            files)
      -w, --use-virtualenvwrapper
                            use 'mkvirtualenv' and 'workon' from virtualenvwrapper
      --virtualenvwrapper-name=VIRTUALENVWRAPPER_NAME
                            the name of the virtualenvwrapper environment to use
                            (defaults to project_name)
      --virtualenvwrapper-path=VIRTUALENVWRAPPER_PATH
                            the path to the virtualenvwrapper
