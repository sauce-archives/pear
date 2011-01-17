PEAR Channel Server hosted by GitHub
====================================

This is the Sauce Labs PEAR Channel Server hosted by GitHub and powered by [Pirum](http://www.pirum-project.org)

Inspired by jsor's PEAR channel [jsor.github.com/pear](http://jsor.github.com/pear)

Create your own PEAR Channel Server
-----------------------------------

 1. Create a new repository on GitHub called `pear` (or any other name)
 2. Create a local git repository (use the same name from the previous step and replace `[username]` with your GitHub username)
        $ mkdir pear
        $ cd pear
        $ git init
        $ git remote add origin git@github.com:[username]/pear.git
 3. Install [Pirum](http://www.pirum-project.org)
        $ pear channel-discover pear.pirum-project.org
        $ pear install pirum/Pirum-beta
 4. Create a configuration file pirum.xml with the following content (replace `[username]` with your GitHub username)
        <?xml version="1.0" encoding="UTF-8" ?>
        <server>
          <name>[username].github.com/pear</name>
          <summary>[username]'s PEAR Channel Server</summary>
          <alias>[username]</alias>
          <url>http://[username].github.com/pear</url>
        </server>
 5. Run the build command
        $ pirum build .
 6. Now add and commit everything
        $ git add .
        $ git commit -m "Initial server build"
 7. Rename your master branch to gh-pages and push it to GitHub
        $ git branch -m master gh-pages
        $ git push origin gh-pages
 8. Your PEAR channel server is now available under `[username].github.com/pear`. You can test it with (replace `[username]` with your GitHub username)
        $ pear channel-discover [username].github.com/pear
        $ pear channel-info [username]
        $ pear list-all -c [username]

Add packages to your PEAR Channel Server
----------------------------------------

 1. Add a PEAR package
        $ pirum add . My_Package-1.0.0.tgz
 2. Add, commit and push everything to publish the new package
        $ git add .
        $ git commit -m "Add 1.0.0 release of My_Package"
        $ git push origin gh-pages
