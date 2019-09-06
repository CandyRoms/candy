Welcome to CandyRoms
===================


Begin tasting the sweetness
---------------

To get started with CandyROMs based on Android 10, you'll should be familiar with
[Git and Repo](https://source.android.com/source/using-repo.html) and the basics of internal Android functionality.

Please set up your build environment by following the [AOSP guide](https://source.android.com/setup/build/initializing). You might want to take
a look at @akhilnarang's scripts [here](https://github.com/akhilnarang/scripts).

To initialize your local repository using the Candy c10 trees, use this command:


	repo init -u git://github.com/CandyROMs/candy.git -b staging/c10


Then sync up with this command:

	repo sync

Additional flags which you can append to speedup the sync process are:

    repo sync --force-sync -c --no-tags --no-clone-bundle --optimized-fetch --prune -j$(nproc)

Submitting Patches
------------------

We're open source, and patches are always welcome!
To do this, you will need an account setup with our gerrit server and add changeid hooks.
To add changeid hook, use the following commands:

	cd <project>
	scp -p -P 29418 <username>@gerrit.bbqdroid.org:hooks/commit-msg .git/hooks/

You can also install the hook globally in all local CandyRoms projects:

    repo forall -c 'gitdir=$(git rev-parse --git-dir); scp -p -P 29418 <username>@gerrit.bbqdroid.org:hooks/commit-msg ${gitdir}/hooks/'

You can send patches by using these commands:

    cd <project>
    git add .
    git commit
    git push ssh://<username>@gerrit.bbqdroid.org:29418/CandyRoms/<project> HEAD:refs/for/<branch>

    OR

    cd <workspace>
    repo upload CandyRoms/<project>

This will commit your changes into a single commit.
Make sure your git has the changeid hooks added.
If you are going to make extra additions, just repeat steps (Don't repo start again), but instead of

	git commit

use

	git commit --amend

Gerrit will recognize it as a new patchset.

To view the status of your and others patches, visit [CandyRoms Code Review](http://gerrit.bbqdroid.org)


Official Device Support
-----------------------

We only support the devices we own.

If you are interested in becoming an "official" Device Maintainer or a part of the team, you are welcome, but we have some basic expectations of a DM, but nothing too crazy.  We want to avoid "one hit wonders" that come and go just as fast. So be prepared to show us at least a few months of your source code activities, with proper authorship. You should also be able to use Gerrit code review to push and pick/pull changes.

If you are a device maintainer, want to build/support your device on CandyRoms, and can meet our DM requirements please contact us to be considered. 

We mostly need to see some history of your activity, how you use Github (and Gerrit), and maintain authorship.  User interaction is considered too, as well as bug fixing and timeframes to do so, so a release channel where you post your work should be present.
