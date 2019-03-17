# Pasta

Command line tool to check if copy-pasted code has been updated in the source since you or your team added it. Name inspired by copy pasta and spagetti code.

## NOTE: not yet implemented!

This repo is currently just a idea. Feedback is appreciated. I plan to implement it as a cli tool written in Go and distribute as a single binary.

## Why would you use Pasta?

If you tend to copy code or find implementation inspiration from other packages, repos, stack overflow or medium posts and you want to know if it has been updated since it was added.

Pasta is not a dependency or package manager. It simply provides a structured way of keeping track of copy pasta code sources (called ingredients).

All Pasta does is tell you if it seems like there was an update or not. It does not diff or update your code, but it will tell you that there might be new performance, security or other improvements implemented in the source.

In the age of gitops, everything as code and huge amounts of open source code ready and available, it makes sense to reuse what other has done. Not everything is available as importable packages!

Use Pasta to track where the inspiration for your code comes from. If you reuse a class, a method or a strategy from someone elses codebase, package or blog post, add an ingredient reference and let Pasta keep track of the source and if it has been updated.

## How to use it

Add comments in your code and run Pasta to timestamp it.

```<comment token> pasta <ingredient> [timestamp] [stale code]```

* `comment token` - the usual comment characters like `//`, `/*`, `#`, `<!--`
* `ingredient` - source url of the code. Like a github repo/folder/file, stack overflow question/comment or medium post. Added by the dev.
* `timestamp` - when the resource was init or updated. Managed by Pasta.
* `state` - Code that indicates the state of an ingredient. Managed by Pasta. Example codes: STALE, UNRESOLVABLE, IGNORE(D)

## Example usage

Insert a comment in your code like

```# pasta github.com/some/repo/blob/path/and/file.go```

Then use Pasta to keep track of the ingredients and if they have been updated since timestamp

### Commands

* `pasta init` - set an initial timestamp for pasta ingredients that are missing timestamps
* `pasta check` - check all non-stale ingredients if they are stale
* `pasta update` - update the timestamp for all stale ingredients
* `pasta list` - display all ingredients and their state

## How it would work

Pasta would check for Pasta comments recursively in the current directory and for each of those ingredients try to figure out a last updated timestamp.
It would then compare that against the timestamp in the Pasta comment and notify the user if it has been updated.
