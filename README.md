# depot_tools

This package contains tools for working with Chromium development. It requires
python 2.7.


## Tools

The most important tools are:

- `fetch`: A `gclient` wrapper to checkout a project. Use `fetch --help` for
  more details.
- `gclient`: A meta-checkout tool. Think
  [repo](https://source.android.com/source/using-repo.html) or [git
  submodules](https://git-scm.com/docs/git-submodule), except that it support
  OS-specific rules, e.g. do not checkout Windows only dependencies when
  checking out for Android. Use `gclient help` for more details and
  [README.gclient.md](README.gclient.md).
- `git cl`: A code review tool to interact with Rietveld or Gerrit. Use `git cl
  help` for more details and [README.git-cl.md](README.git-cl.md).
- `roll-dep`: A gclient dependency management tool to submit a _dep roll_,
  updating a dependency to a newer revision.

There are a lot of git utilities included.


## Updating

`depot_tools` updates itself automatically when running `gclient` tool. To
disable auto update, set the environment variable `DEPOT_TOOLS_UPDATE=0`.

To update package manually, run `update_depot_tools.bat` on Windows,
or `./update_depot_tools` on Linux or Mac.

On Windows only, running `gclient` will install `git` and `python`.  


## Contributing

To contribute change for review:

    git new-branch <somename>
    # Hack
    git add .
    git commit -a -m "Fixes goat teleporting"
    # find reviewers
    git cl owners
    git log -- <yourfiles>

    # Request a review.
    git cl upload -r reviewer1@chromium.org,reviewer2@chromium.org --send-mail

    # Edit change description if needed.
    git cl desc

    # If change is approved, flag it to be commited.
    git cl set-commit

    # If change needs more work.
    git rebase-update
    ...
    git cl upload -t "Fixes goat teleporter destination to be Australia"


### cpplint.py

To update cpplint.py, please submit the change upstream first at
https://github.com/google/styleguide/tree/gh-pages/cpplint then copy it down.
