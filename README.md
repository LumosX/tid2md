# tid2md

Migrate your TiddlyWiki5 (Node.js version) tiddlers (`.tid` files) to Markdown tiddlers (`.md` files for markup plus `.md.meta` files for meta information).


## Markdown in TiddlyWiki

[TiddlyWiki](https://tiddlywiki.com/) uses its own [WikiText](https://tiddlywiki.com/#WikiText) markup language. While this is the natural first choice when using TiddlyWiki, it's also possible writing tiddlers in Markdown using the official [Markdown Plugin](https://tiddlywiki.com/#Markdown%20Plugin). Markdown has the advantage that it's used in many places (p.e. GitHub, GitLab, BitBucket, StackOverflow, Reddit) and is supported by many editors, parsers and other tools. When you often copy tiddlers (or parts of them) to other websites or when you edit/process your `.tid` files with tools except TiddlyWiki itself, it might make sense to write your tiddlers in Markdown or migrate those already written in WikiText to Markdown. This is what `tid2md.py` was made for.


## Differences from base version
This is a fork from the real version at [MaxGyver83/tid2md](https://github.com/MaxGyver83/tid2md). The differences from the base version, at the time of writing (11/09/2023), are:

* Works with tiddlers containing unicode characters (base PR [#4](https://github.com/MaxGyver83/tid2md/pull/4))
* One URL-parsing bug fixed (base PR [#5](https://github.com/MaxGyver83/tid2md/pull/5))
* Uses angle brackets for links instead of ruining them with URL-encodings (no %20s instead of spaces) (base PR [#6](https://github.com/MaxGyver83/tid2md/pull/6))
* No header verification. (base issue [#2](https://github.com/MaxGyver83/tid2md/issues/2)) This version won't check for headers, and will assume every tiddler you're trying to migrate begins with a proper header.

Ideally all these fixes, and a fix for the header problem, will have been added to the real version by the time you read this, and you can just ignore this fork. I'm certainly not going to be maintaining it.


## Usage
Download the python file and drop it into the directory you're seeking to migrate (e.g. `tw-wiki\tiddlers`). Open your terminal and possibly activate any environment you're running. Then just run the script:

On powershell:

`python .\tid2md.py -d *.tid` 

The `-d` flag will wipe all original files. `*.tid` is any pattern, will be globbed. Absolute paths will work, if your tid files are not in the same folder as the script.

You can use the `--no-angle-brackets` flag if you don't want to use angle-bracket links and want to use URL-encoded links instead, for some reason.

I recommend backing up your tiddlers folder, running this script on the new copy, checking everything out, and proceeding only then. Definitely make a backup though.