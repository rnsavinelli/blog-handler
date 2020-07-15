# nlb -- Nicolás's Luke's Blog Script (Nicolas's lb)

Blogs and RSS feeds in about 100 lines of shell script.

Published and distributed as a modified version of [Luke Smith's lb](https://github.com/LukeSmithxyz/lb) (and under the same license), nlb is an improved, and not so slim version, of it catered for my needs. 

For a list of all changes made to the original script see the [`CHANGELOG`](https://github.com/rnsavinelli/nlb/blob/blog/CHANGELOG).

For licensing details, distributability and modifyability refer to the [`LICENSE`](https://github.com/rnsavinelli/nlb/blob/blog/LICENSE) file.

## Features

`nlb` is an extremely small shell script that lets you write blog posts and will format them in all the ways you could ever want. Here's what it will produce:

- A Rolling Blog Page. See [my own Rolling Page](https://rnsavinelli.github.io/blog.html) as an example.
- A list of all blog entries with dates: [Blog List File](https://rnsavinelli.github.io/blogindex.html).
- All your blog posts appear as standalone entries/pages, for example [like this one](https://rnsavinelli.github.io/blog/now-plotting-network-traffic.html).
- These standalone files exist in a `blog/` directory, which you can allow to be browsed manually via your Apache web server as Luke Smith has [here](http://lukesmith.xyz/blog).
- Blog posts are added, in full form, to an RSS feed of your chosing as well, see [my RSS feed](https://rnsavinelli.githu.io/rss.xml).
- Posts in the rolling blog have divs that can easily be modified via a CSS stylesheet, and in general everything is easily editable.
- One command to delete published entries from the RSS feed, rolling blog and standalone entries simultaneously.
- Published blog entries can now be revised, updating the standalone blog pages, the RSS feed and everything else.

## Usage

`nlb` commands are all one letter cause its simpler. They all stand for something though.

```sh
./nlb n(ew)	# Make a new blog post draft.
./nlb e(dit)	# Edit a draft of an entry.
./nlb t(rash)	# Delete a draft of an entry.
./nlb p(ublish)	# Finalize/publish a blog post draft.

./nlb d(elete)	# Delete a published blog post.
./nlb r(evise)	# Revise an already published entry (you can republish it with `nlb p` when done).

./nlb l(ist)	# List all drafts.
./nlb h(istory)	# List published entries (publication history)
```

## Installation

+ bash and GNU sed is required.
+ Be sure that you own or have writing privileges in the given directory, so the script can create the required directory structure.
+ Download the `nlb` script and put it in your website's main directory. The expectation is that your rolling blog file and RSS feed will be there as well.
+ Open the script and change the first few variables to match the names of the files you use in your website.
+ Add markers for where the new blog posts are added. **Don't skip this step.** See below.

### Markers

IMPORTANT: Unmodified to grant backwards compatibility with `lb`.

For the system to work, add the following comment line to a (1) Rolling Blog File (as above), a (2) Blog List File and (3) RSS feed.

```
<!-- LB -->
```

You can format these files/pages how ever you want, just be sure to edit the `nlb` file and change the variables at the top to match the file names of those you chose.

When you `finalize` a blog post, it will be added directly below that line in the proper format (either HTML or the proper RSS/XML format), give you the rolling blog and RSS feed for free.

## Info

- The blog entries are stored in `blog/` in your websites root directory. Drafts are in `blog/.drafts`.
- `blog/.htaccess` acts as a "database" file. `nlb` stores filenames with their corresponding proper names and publishing dates there.
- The other files in this repo just illustrate how you can use `nlb`. Only the `nlb` script itself is necessary.
- Your `$EDITOR` variable should be set to your preferred text editor, vim will be assumed if you don't have one set.
