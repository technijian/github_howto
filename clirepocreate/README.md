# Create repo

## Overview

TODO:

Create a repo from the CLI ...be sure to use http not ssh on the "git remote add origin "https://github.com/your_github_username/$repo_name.git"

	#!/bin/sh

	repo_name=$1
	test -z $repo_name && echo "Repo name required." 1>&2 && exit 1

	curl -u 'your_github_username' https://api.github.com/user/repos -d "{\"name\":\"$repo_name\"}"

As mentioned in the comments, don't forget to make the above script executable by running chmod +x git-create.

Make sure you save it somewhere on your PATH. If you don't have a directory for custom shell scripts on your PATH, you can save it in ~/bin and then add that to your PATH by editing ~/.bash_profile as follows:

	PATH=$PATH:~/bin
	export PATH

Now you can easily create a new github repo from with the following command:

	git create mynewrepo

If you assume this command is run from a valid local git repo (or the folder containing what should become the repo) you can add the following lines to "git-create" to automatically add the remote:

	git init
	git remote add origin "https://github.com/your_github_username/$repo_name.git"
	git push -u origin master (enter your username/password for https auth)
git init is safe and won't mess anything up if the local repo already exists.

Enjoy!
