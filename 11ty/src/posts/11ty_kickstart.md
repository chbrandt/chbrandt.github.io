---
title: 11ty Kickstart
# templateEngineOverride: md
---

> This note is basically the transcription of excelent video-tutorial
> ["Build an 11ty Site in 3 Minutes"](https://youtu.be/BKdQEXqfFA0?si=JpP1TBlvf4lMxnTg)
> in *11ty Rocks!* YouTube channel.

* Install 11ty:
```bash
npm init -y
npm install @11ty/eleventy --save-dev
```

* Set commands for *start/build* in `package.json`.

`package.json`:
```json
{
  "name": "chbrandt.github.io",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "start": "eleventy --serve",
    "build": "eleventy"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@11ty/eleventy": "^2.0.1"
  }
}
```

* Update Input/Output directory

```bash
touch .eleventy.js
```

`.eleventy.js`:
```javascript
module.exports = function (eleventyConfig) {
    return {
        dir: {
            input: "src",
            output: "public"
        }
    };
};
```

Create directories:
```bash
mkdir src public
```

* Create Index and Layout files. Using layouts from the start is recommended.

Layouts are expected to be in `src/_includes` directory (nunjucks file):
```bash
mkdir src/_includes
touch base.njk
```

`base.njk`:
```html
{% raw %}
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>{{ title }}</title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- <link rel="stylesheet" href=""> -->
</head>

<body>
    <header>
        <h1>{{ title }}</h1>
    </header>
    <main>
        {{ content | safe }}
    </main>
</body>

</html>
{% endraw %}
```

Create `index.md`:
```bash
touch src/index.md
```

`index.md`:
```markdown
---
title: Hallo Welt
layout: "base.njk"
---

Hallo, Carlos!
```

* Run 11ty

Start eleventy:
```bash
npm start
```

See in the browser at `localhost:8080`.


* Add some style

Create css file:
```bash
touch src/style.css
```

`style.css`:
```css
body {
    font-family: sans-serif;
}
```

Include the stylesheet in the (html) template, make sure line:
```html
<link rel="stylesheet" href="style.css">
```
is in the `<head>` section.

Then we have to make 11ty aware of the CSS file by editing the config,
`.eleventy.js`:
```js
module.exports = function (eleventyConfig) {
    eleventyConfig.addPassthroughCopy("./src/style.css");

    return {
        dir: {
            input: "src",
            output: "public"
        }
    };
};
```

* Create a blog

Create `posts/` directory:
```bash
mkdir src/posts
touch src/posts/11ty_kickstart.md
```

`11ty_kickstart.md`:
```markdown
---
title: 11ty Kickstart
---

First post
```

Add a directory data file, create a `posts.json` file in `posts/`:
```bash
touch src/posts/posts.json
```

Configure `base.njk` layout per default and tag *#posts*:

`posts.json`:
```json
{
    "layout": "base.njk",
    "tags": "posts"
}
```

Update `index.md` to include posts:

`index.md`:
```markdown
{% raw %}
---
title: Hallo Welt
layout: "base.njk"
---

Hallo, Carlos!

{% for post in collections.posts %}

- [{{ post.data.title }}]({{ post.url }})

{% endfor %}
{% endraw %}
```
