git-release(1) -- Commit, tag and push changes to the repository
================================================================

## SYNOPSIS

`git-release` &lt;tagname&gt; [-r &lt;remote&gt;] [-m &lt;commit info&gt;] [-c] [[--] &lt;hook arguments...&gt;]

## DESCRIPTION

  Commits changes with message "Release &lt;tagname&gt;" or custom commit information, tags with the given &lt;tagname&gt; and pushes the branch / tags.

  Optionally it generates a changelog (see git-changelog) and a remote can be defined. The order of first -c or -r does not matter.

  If `.git/hook/pre-release` or `.git/hook/post-release` exist, they will be triggered with `tagname` and extra hook arguments before/after the release.

## OPTIONS

  &lt;tagname&gt;

  The name of the newly created tag. Also used in tag comment.

  -r &lt;remote&gt;

  The "remote" repository that is destination of a push operation: it is passed to git push.

  -m &lt;commit info&gt;

  use the custom commit information instead of the default message "Release &lt;tagname&gt;" .

  -c

  Generates or populates the changelog with all commit message since the last tag. For more info see git-changelog..

  [--] hook arguments...

  The arguments listed after "--" separator will be passed to pre/post-release hook following the `tagname`.

## EXAMPLES

  * Release commit with the given &lt;tagname&gt;.

    $ git release 0.1.0

  * Release commit with the given &lt;tagname&gt; and custom commit message.

    $ git release 0.1.0 -m "+ powerful feature added."

  * Release commit with the given &lt;tagname&gt; and push to specific remote.

    $ git release 0.1.0 -r github

  * Release commit with the given &lt;tagname&gt; and populate changelog.

    $ git release 0.1.0 -c

  * Release commit with the given &lt;tagname&gt;, populate changelog, and push to specific remote.

    $ git release 0.1.0 -r github -c

  * Release commit with the given &lt;tagname&gt;, pass &lt;tagname&gt; and extra argument to release hook,
    populate changelog, and push to specific remote.

    $ git release 0.1.0 -r github -c -- --signature-required


## AUTHOR

Written by Tj Holowaychuk &lt;<tj@vision-media.ca>&gt;
Extended by David Hartmann &lt;<dh@tsl.io>&gt;

## REPORTING BUGS

&lt;<https://github.com/tj/git-extras/issues>&gt;

## SEE ALSO

&lt;<https://github.com/tj/git-extras>&gt;
