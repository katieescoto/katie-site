Steps to get items to deploy to Pantheon:
- [ ] On Pantheon, set up a Pantheon site.
- [ ] In the repo, give `env.dist` a TERMINUS_SITE and TS_HOST_REPO
- [ ] On Circle, add the project you just created to the list of builds: https://circleci.com/add-projects/gh/thinkshout
- [ ] On Circle, add the "Pantheon - ThinkShout CI Bot" (1password) Private-key to the circle.ci ssh permissions: https://circleci.com/gh/thinkshout/[YOUR PROJECT]/edit#ssh
- [ ] In Circle.ci, add the PANTHEON_TOKEN associated with the "Pantheon - ThinkShout CI Bot" (1password) to the circle.ci Environment variables tab: https://circleci.com/gh/thinkshout/[YOUR PROJECT]/edit#env-vars 
- [ ] On Circle turn on the “Auto-cancel redundant builds” option under https://circleci.com/gh/thinkshout/[YOUR-PROJECT]/edit#advanced-settings
- [ ] In the repo (`.circleci/config.yml`), if you wish to run phpcs tests (you do) uncomment the "Run CS tests" commands. Then replace every instance of `drupal-project` in `behat/behat.ci.yml` with the name of your repo.
- [ ] In the repo (`.circleci/config.yml`), if you wish to deploy to Pantheon for ease of testing, you can uncomment out the `-deploy` step. Note: By default this command re-installs your site with each push. If you'd like to just push code but not wipe the database, change the line from `robo pantheon:deploy --install --y` to `robo pantheon:deploy --y`
- [ ] In the repo (`.circleci/config.yml`), find and replace any instances of `drupal-project` in your config.yml file with the name of your repo.
