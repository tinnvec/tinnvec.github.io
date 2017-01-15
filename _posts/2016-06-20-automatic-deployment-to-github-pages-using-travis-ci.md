---
layout: post
title: Automatic deployment to Github Pages using Travis CI
date: 2016-06-20 14:30:00 -0500
categories:
    - programming
    - deployment
tags:
    - github pages
    - travis ci
---
Working with [decal](https://github.com/tinnvec/decal), I have the need to host a very simple HTML5/JavaScript site.
This can be very easily done with Github Pages, but I can't be bothered to update the `gh-pages` branch manually every
time I update the underlying source code.
<!-- more -->

Enter [Travis CI](https://travis-ci.org/) to  save the day. A simple `after_success` script can take care of everything.

* Create a [Github personal access token](https://github.com/settings/tokens) with `public_repo` permissions.
* On [Travis CI](https://travis-ci.org/), add the `GITHUB_API_TOKEN` environment variable under settings for your repository, setting it's value to the token you just made.
* In the project's `.travis.yml` file, execute your script in the `after_success` block as shown below

```yaml
# .travis.yml
after_success: bash ./autodeploy.sh
```

* Create `autodeploy.sh` as shown below (note: replace `<github_username>` and `<github_repo>` with your info)

{% gist 8eeec36e2119128d201a018d2d924405 %}
