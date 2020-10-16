# blog-handler - rnsavinelli's version of lb

Blogs and RSS feeds in less than 150 lines of shell script.

blog-handler is published and distributed as a modified version of [Luke Smith's lb](https://github.com/LukeSmithxyz/lb) under the GPLV3 license.

For a list of all changes made to the original script review the [`CHANGELOG`](https://github.com/rnsavinelli/blog-handler/blob/blog/CHANGELOG).

For licensing details refer to the [`LICENSE`](https://github.com/rnsavinelli/blog-handler/blob/blog/LICENSE) file.

IMPORTANT: This fork will be kept up-to-date with Luke's upstream version as long as updates are proven to be useful, or valuable. For instance, commit [f13cf1a](https://github.com/LukeSmithxyz/lb/commit/f13cf1a3a642dcaa6eb188b15db4e36450edcabd)
seemed to be an improvement at first, but it ended up obfuscating the user's experience. See pull request [#35](https://github.com/LukeSmithxyz/lb/pull/35) and commit [66e2a7a](https://github.com/LukeSmithxyz/lb/commit/66e2a7a1eda6d835266d8ad62270d87b50ee488c) for more details.

## Features

`blog-handler` is an extremely small shell script that lets you write blog posts and will format them in all the ways you could ever want. Here's what it will produce:

- A Rolling Blog Page. See [my own Rolling Page](https://rnsavinelli.github.io/blog.html) as an example.
- A list of all blog entries with dates: [Blog List File](https://rnsavinelli.github.io/blogindex.html).
- Idem but for the website's index: [my own Index Page](https://rnsavinelli.github.io/index.html).
- All your blog posts appear as standalone entries/pages, for example [like this one](https://rnsavinelli.github.io/blog/now-plotting-network-traffic.html).
- These standalone files exist in a `blog/` directory, which you can allow to be browsed manually via your Apache web server.
- Blog posts are added, in full form, to an RSS feed of your chosing as well, see [my RSS feed](https://rnsavinelli.github.io/rss.xml).
- Posts in the rolling blog have divs that can easily be modified via a CSS stylesheet, and in general everything is easily editable.
- One command to delete published entries from the RSS feed, rolling blog and standalone entries simultaneously.
- Published blog entries can now be revised, updating the standalone blog pages, the RSS feed and everything else.

## Usage

`blog-handler` commands are all one letter cause its simpler. They all stand for something though.

```sh
./blog-handler n(ew)	# Make a new blog post draft.
./blog-handler e(dit)	# Edit a draft of an entry.
./blog-handler t(rash)	# Delete a draft of an entry.
./blog-handler l(ist)	# List all drafts.
./blog-handler p(ublish)	# Finalize/publish a blog post draft.

./blog-handler d(elete)	# Delete a published blog post.
./blog-handler r(evise)	# Revise an already published entry (you can republish it with `blog-handler p` when done).
./blog-handler h(istory)	# List published entries (publication history)
```

## Installation

+ bash and GNU sed is required.
+ Be sure that you own or have writing privileges in the given directory, so the script can create the required directory structure.
+ Download the `blog-handler` script and put it in your website's main directory. The expectation is that your rolling blog file and RSS feed will be there as well.
+ Open the script and change the first few variables to match the names of the files you use in your website.
+ Add markers for where the new blog posts are added. **Don't skip this step.** See below.

### Markers

IMPORTANT: `lb` markers were NOT modified to grant backwards compatibility.

For the system to work, add the following comment line to a (1) Rolling Blog File (as above), a (2) Blog List File, a (3) Index File, and (4) RSS feed. See the example files provided with `blog-handler` to have a better picture.

```
<!-- LB -->
```

You can format these files/pages how ever you want, just be sure to edit the `blog-handler` file and change the variables at the top to match the file names of those you chose.

When you `finalize` a blog post, it will be added directly below that line in the proper format (either HTML or the proper RSS/XML format), give you the rolling blog and RSS feed for free.

## Info

- The blog entries are stored in `blog/` in your websites root directory. Drafts are in `blog/.drafts`.
- `blog/.htaccess` acts as a "database" file. `blog-handler` stores filenames with their corresponding proper names and publishing dates there.
- The other files in this repo just illustrate how you can use `blog-handler`. Only the `blog-handler` script itself is necessary.
- Your `$EDITOR` variable should be set to your preferred text editor, vim will be assumed if you don't have one set.

## About the theme

The Bootstrap theme is a modified version of [Bootswatch's Sandstone theme](https://bootswatch.com/sandstone/) and it inherits its MIT License.
To contibute to Bootswatch themes development consider visiting the https://github.com/thomaspark/bootswatch repository.
