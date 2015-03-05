# Local Django Environment Setup Best Practices

1. Use the same database engine everywhere
  * Don't use MySQL or SQLite in your development environment, and PostgreSQL in production.
2. Use **virtualenv** or **virtualenvwrapper** (or **pyvenv**, included in Python 3)
3. Use **pip** to install Django and dependencies
4. Use **git** to keep all development and production files version controlled.
  * Set up a remote repository, in addition to your local repo. Bitbucket and Github are the most popular, and have their own strongpoints.
5. Consider using Vagrant for local development. 
