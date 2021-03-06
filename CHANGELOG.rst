0.3.2
-----
- Fixed a bug in vcs url templating.
- Improved the performance of git-bloom-config.
- Added an --unsafe global option which will disable some of the safety mechanisms in bloom, making releasing about twice as fast but at the expense of errors putting the local release repository in an inconsistent state. Use with caution.
- Added support for templating stack.xml files like package.xml files in the import-upstream step.
- Fixed a bug where bloom failed if you call it and you were not on a branch
- Added global arguments to some commands which were still lacking them
- Fixed a bug where bloom would create None/<version> tags (these should be deleted manually if found)
- Got the automated tests fixed and running in travis again
- Added emoji icons for OS X users with lion or greater

0.3.1
-----
- Fixed handling of non-standard archive names in git-bloom-import-upstream.
  This was a bug where if the archive only had the name of the package then it would fail to be processed by import-upstream.
- Fixed an issue when blooming from svn upstream.
  This issue was caused by improperly handling the release_tag configuration when dealing with svn

0.3.0
-----
- Generators can now be added using the distribute entry_points machanism
- There is now a debian/<rosdistro>/<package_name> branch before forking into debian/<rosdistro>/<debian_distro>/<package_name>
  The debian/<rosdistro> branch now contains the untemplated debain files, so that they can be patched before being templated.
- Users are now dropped into a shell when patch merging fails, allowing them to resolve the problem and continue.
- New generator rosrelease, makes the release tag release/<rosdistro>/<package_name> instead of release/<package_name>
- Bloom now checks to see if it is the latest version available and warns if it is not
- Configurations are now stored in "tracks" so that there can be multiple release configurations in each release repository
- New command bloom-export-upstream, this command creates an archive (tar.gz) of upstream given a uri, type, and reference to archive
- Refactored git-bloom-import-upstream, this command only takes an archive (tar.gz) now
- Configurations are now stored on the bloom branch in YAML
- git-bloom-release now takes only one argument, the release track to execute
- Files can be automatically overlaid onto upstream using a patches folder in the bloom branch
  This allows you to put a package.xml onto upstream without a patch in the release branch.
- package.xml files overlaid onto upstream branch from the patches folder in the bloom branch are templated on the version
- Release tags now contain release increment numbers, similar to the debian increment numbers, e.g. release/groovy/foo/0.1.0 is now release/groovy/foo/0.1.0-0
- New command bloom-release <repository> [<track>], which will release a repository end-to-end
  It will fetch the release repository using info from the ROS distro file, run bloom, then push the results


