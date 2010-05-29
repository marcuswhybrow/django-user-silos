Django User Silos
=================

The Story
---------

Django User Silos is the solution to a specific problem. When creating [MyUni](http://github.com/robgolding63/myuni/) - A centralised portal for university students - we wanted to be able to support all universities under a single hosted service which they would subscribe to.

In addition we wanted to maintain each students original university wide username and password. This is achieved through a custom authentication backend, however the users of the system (the students and lectures) will need to be represented as objects in Django at some point.

Here arises the problem. Two different universities may have conflicting usernames. The problem is a simple one to identify put more complicated to amend.

The Solution
------------

By replacing the `django.contrib.auth` app with this one you are changing a few things. First every `User` object now has a new attribute called `silo`. This is a one to many relationship with a `Silo` object. A `Silo` has a few fields of its own, but what is important is that a `User` object's `username` and `silo` attributes must be unique together.

In the case of _MyUni_ a `University` model then has a one to one attribute called `silo` linking it to its users.

Installation
------------

This project is not yet ready to be put into use.