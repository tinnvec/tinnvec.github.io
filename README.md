Hi there.<img src="{{ site.github.owner_gravatar_url }}" width="192" height="192" style="float: right; margin: 5px;" />

I'm Alex (aka tinnvec) and I'm a nerd with a passion for coding starting in the mid-90s.

Currently, I use a lot of C# and .NET at work but tend to prefer JavaScript and Ruby for personal projects. Though I have my favorites, I'm always learning new things I find interesting (this site is done in Jekyll, for example).

# GitHub Projects
{% assign sorted_repos = site.github.public_repositories | sort:"pushed_at" | reverse %}
{% for repository in sorted_repos %}
* [{{ repository.name }}]({{ repository.html_url }}){% endfor %}

# Contact

* [tinnvec@gmail.com](mailto:tinnvec@gmail.com)
* [Discord](https://discordapp.com/): tinnvec#3217
* [Battle.net](https://battle.net/): Tinnvec#1493

## Social

* [GitHub]({{ site.github.owner_url }})
* [StackExchange](https://stackexchange.com/users/5352118/tinnvec/)
* [LinkedIn](https://www.linkedin.com/in/tinnvec/)
* [YouTube](https://www.youtube.com/tinnvec/)
* [Twitch](https://twitch.tv/tinnvec/)
