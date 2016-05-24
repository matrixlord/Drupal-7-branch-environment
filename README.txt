This is a script that runs as a git hook after a branch checkout.

It is specific for Drupal 7 and its main use is to create a different DBs and
settings.php files for each branch.

Details:
- It uses post-checkout hook
- It creates a different DB for each branch on checkout
- It creates a backup of settings.php file for every branch, in the format
  settings_${branchName}.php
- The DB is copied from the "master" DB

Use case:
- Before anything, be sure to have checked out the master branch of your project
- Set the original DB of your Drupal 7 project as {prefix}master, where prefix
  is the name of your project. e.g. my_new_eshop_master. In this case the
  "my_new_eshop_" is the prefix
- Copy "post-checkout" file into ".git/hooks/" folder in your Drupal 7 project
- Change inside the file "dbPrefix" variable to your DB prefix
  e.g. "my_new_eshop_"
- Set in "post-checkout" file the root username and password
- Set in "post-checkout" file the user that is connected to the DB from Drupal
  in "dbUserAccess". This is the DB user that Drupal uses to connect to the DB
