Environments
============

The following environments are available for this project:

Deployment hooks
----------------

  * npm run package

This hook is called during the packaging of the rpm file. In that script, the basics things to do are to install the dependencies, and build your application. If you want to make the package smaller, you can remove useless things for production like the client sources, the dev modules, etc.

  * npm run postdeploy

This hook is called during the deployment on the server. It should be used to migrate your database, load fixtures, etc. It's called after the installation of the application on the server but before starting it.

Deploy to staging for the first time
-----------------


Fast-deploy to staging
-----------------

