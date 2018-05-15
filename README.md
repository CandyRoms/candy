CandyRoms
=========

To initialize your local repository, use this command:

	repo init -u https://github.com/CandyRoms/candy.git -b c8.1

Continue to sync Candy by issuing:

	repo sync --force-sync --no-tags --no-clone-bundle -jX (X depends on the number of cores your CPU has, and the strength of your connection)

Submitting Patches
------------------

We're open source, and patches are always welcome!
To do this, you will need an account setup with our gerrit server and a changeid hooks.
To add the changeid hook in a project, use the following commands:

	cd <project>
	scp -p -P 29418 <username>@gerrit.bbqdroid.org:hooks/commit-msg ${gitdir}/hooks/

You can also install the hook globally in all local CandyRoms projects

	repo forall -c 'gitdir=$(git rev-parse --git-dir); scp -p -P 29418 <username>@gerrit.bbqdroid.org:hooks/commit-msg ${gitdir}/hooks/'

Go have a coffee while this runs

You can send patches by using these commands:

    cd <project>
    git add --all
    git commit
    git push ssh://<username>@gerrit.bbqdroid.org:29418/CandyRoms/<project> HEAD:refs/for/<branch>

This will commit your changes into a single commit.
Make sure your git has the changeid hooks added.
If you are going to make extra additions, just repeat steps, but instead of

	git commit

use

	git commit --amend

Gerrit will recognize it as a new patchset.

Maintaining Authorship
----------------------

When pushing a new commit or patch/fix, you need to add the original author before pushing to gerrit. This can be done by adding --author when amending the commit. 

	git commit --amend --author "Author Name <authoremail@address.com>"

For example, if Dan is the author of the commit!

	git commit --amend --author "Dan Cartier <nospamdan1@gmail.com>"

Maintaining Authorship is very important in the Android open source community. If you dont want to be called a kanger or face backlash from the community, you need to give proper authorship!

If you want to keep the original date of the commit, you can do so by adding --date="time". For example:

	git commit --amend --date="Thu, 5 Apr 2018 17:53:07 +0545"

If you want to see every information about the commit, add .patch at the end of the commit link.
Like: https://github.com/CandyRoms/candy/commit/6bce46aa80ef72db130ab0b61a98f8b8e40c655f.patch

To view the status of your and others patches, visit [CandyRoms Code Review](http://gerrit.bbqdroid.org)
