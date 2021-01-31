Flask-NeoAlchemy
================

Flask-NeoAlchemy is an extension for `Flask`_ that adds support for
`py2neo/Neo4J`_ to your application. It aims to simplify using py2neo
with Flask by providing useful defaults and extra helpers that make it
easier to accomplish common tasks.

.. _Flask: https://palletsprojects.com/p/flask/
.. _py2neo: https://www.py2neo.org


Installing
----------

Install and update using `pip`_:

.. code-block:: text

  $ pip install -U Flask-NeoAlchemy

.. _pip: https://pip.pypa.io/en/stable/quickstart/


A Simple Example
----------------

.. code-block:: python

    from flask import Flask
    from flask_neoalchemy import NeoAlchemy

    app = Flask(__name__)
    app.config["NEO4J_DATABASE_URI"] = "bolt://neo4j:neo4j@host:7687/neo4j"
    db = NeoAlchemy(app)


    class User(db.Model):
        id = db.Property(db.Integer, primary_key=True)
        username = db.Property(db.String, unique=True, nullable=False)
        email = db.Property(db.String, unique=True, nullable=False)


    db.session.add(User(username="Flask", email="example@example.com"))
    db.session.commit()

    users = User.query.all()


Contributing
------------

For guidance on setting up a development environment and how to make a
contribution to Flask-NeoAlchemy, see the `contributing guidelines`_.

.. _contributing guidelines: https://github.com/pallets/flask-neoalchemy/blob/master/CONTRIBUTING.rst


Donate
------

The Pallets organization develops and supports Flask-NeoAlchemy. In
order to grow the community of contributors and users, and allow the
maintainers to devote more time to the projects, `please donate today`_.

.. _please donate today: https://palletsprojects.com/donate


Links
-----

-   Documentation: https://flask-neoalchemy.palletsprojects.com/
-   Releases: https://pypi.org/project/Flask-NeoAlchemy/
-   Code: https://github.com/pallets/flask-neoalchemy
-   Issue tracker: https://github.com/pallets/flask-neoalchemy/issues
-   Official chat: https://discord.gg/t6rrQZH
