# Eleventy Website

I want to build a personal website. One thing in particular I want is my
Resumè nicely and somewhat dynamilly rendered (well, filtering options for
different views of the content).

This repo is quickstarted following the video "Build an 11ty Site in 3 Minutes",
from *11ty Rocks!* YouTube channel:

- https://www.youtube.com/watch?v=BKdQEXqfFA0

The tutorial indeed delivers a basic working blog website in great shape in
under 3 minutes. The first blog of this site is the steps presented in the
video, [`src/posts/11ty_kickstart.md`](src/posts/11ty_kickstart.md).


## Notes

Some development/developer notes.

### Turn off template parsing

The first post being the transcription of the video for this site,
the document contains (Liquid) template code.
The contents of `index.md` and `base.njk`, for instance.

Since code blocks in the post is not meant to be parsed, we must disable it.
While the file of the post --a markdown file-- gets rendered.

There is a question about that to which one of the developers (I assume),
answered to the point (https://github.com/11ty/eleventy/discussions/2148).

There are three ways to disable template parsing in a markdown file, and I
[quote](https://github.com/11ty/eleventy/discussions/2148#discussioncomment-1862092):

> - use `markdownTemplateEngine: false` in .eleventy.js config file
>   if you want to disable Liquid-in-Markdown parsing globally.
> - use `templateEngineOverride: md` frontmatter if you want
>   to disable LiquidJS parsing on a per-template basis.
> - use `{% raw %}...{% endraw %}` wrapper if you want
>   to prevent LiquidJS (or Nunjucks) from parsing specific blocks/tags in a file.


/.\
