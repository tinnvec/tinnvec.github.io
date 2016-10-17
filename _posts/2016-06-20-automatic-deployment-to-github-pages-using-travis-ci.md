---
layout: post
title: "Automatic deployment to Github Pages using Travis CI"
date: 2016-06-20 14:30:00 -0500
categories: github-pages travis-ci deployment
---
Working with [decal](https://github.com/tinnvec/decal), I have the need to host a very simple HTM5/JavaScript site.
This can be very easily done with Github Pages, but I can't be bothered to update the `gh-pages` branch manually every
time I update the underlying source code.  
  
Enter [Travis CI](https://travis-ci.org/) to  save the day. A simple `after_success` script can take care of everything. 
  
* Create a [Github personal access token](https://github.com/settings/tokens]) with `public_repo` permissions.
* On [Travis CI](https://travis-ci.org/), add the `GITHUB_API_TOKEN` environment variable under settings for your repository, setting it's value to the token you just made.
* Create `autodeploy.sh` as shown below (note: replace `<github_username>` and `<github_repo>` with your info)
* In the project's `.travis.yml` file, execute your script in the `after_success` block as shown below

{% highlight yaml %}
# .travis.yml
after_success: bash ./autodeploy.sh
{% endhighlight %}

{% highlight bash %}
# autodeploy.sh
if [ -n "$GITHUB_API_KEY" ]; then
    cd "$TRAVIS_BUILD_DIR"

    # Grab SHA for nice linking
    SHA=`git rev-parse --verify HEAD`

    # Move into repository folder with compiled code for gh-pages
    cd public

    # Make a temp git repo
    git init

    # Set git config info for automated changes
    git config user.name "Travis CI"
    git config user.email "$COMMIT_AUTHOR_EMAIL"

    # Add current dir contents to gh-pages branch
    git checkout -b gh-pages
    git add .

    # Commit the stuff
    git commit -m "Deploy to GitHub Pages: ${SHA}"

    # Push it up to gh-pages branch
    # Make sure to make the output quiet, or else the API token will leak!
    # This works because the API key can replace your password.
    git push -f -q  https://<github_username>:$GITHUB_API_KEY@github.com/<github_username>/<github_repo> gh-pages

    cd "$TRAVIS_BUILD_DIR"
fi
{% endhighlight %}