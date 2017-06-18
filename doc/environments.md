Environments
============

The following environments are available for this project:

**Staging**: https://m4.pepinie.re/elvis
  - ***Associated Git branch***: master

Deployment hooks
----------------

  * npm run package

This hook is called during the packaging of the rpm file. In that script, the basics things to do are to install the dependencies, and build your application. If you want to make the package smaller, you can remove useless things for production like the client sources, the dev modules, etc.

  * npm run postdeploy

This hook is called during the deployment on the server. It should be used to migrate your database, load fixtures, etc. It's called after the installation of the application on the server but before starting it.

Deploy to staging for the first time
-----------------

To deploy to staging m4, run the following command from the application folder:
npm run package-push
 - This will package the application and add the image on Nexus.


Deploying uses Ansible provisioning:

``` bash
cd provisioning/ansible

# Pull and install Ansible roles, you will need your GitLab credentials here
 npm run ansible:pull

# Run provisioning command
npm run ansible:provision

# Once the package&push is finished run:
npm run ansible:deploy
```

During your npm run package-push, if you get an error "could not read Username for 'https://github.com': No such device or address", it might be because git is configured through https instead of ssh. Run:
``` bash
  git remote set-url origin git@github.com:theodo/pepiniere-gedsegl-elvis.git
```

Fast-deploy to staging
-----------------

If you deploy frequently, you'll want to avoid the previous method which takes about 10 min.
The fast-deploy runs quickly, without provisioning the server again.

``` bash
  npm run fast-deploy
```
