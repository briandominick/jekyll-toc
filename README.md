# Jekyll Pure Liquid Table of Contents

[![Build Status](https://travis-ci.org/allejo/jekyll-toc.png?branch=master)](https://travis-ci.org/allejo/jekyll-toc)

GitHub Pages can't run custom Jekyll plug-ins so when generating Tables of Contents (TOCs), you're stuck with either a JavaScript solution or using kramdown's `{:toc}` option. However, by using `{:toc}`, you are forced to have that code next to your actual markdown and you can't place it in a layout. This means _every_. _single_. _post_. will need to have the snippet. If you choose the JavaScript approach, that's perfectly fine but what if JS is disabled on the someone's browser or your page is just _really_ long and it becomes inefficient.

Instead, I wrote this solution entirely in Liquid and can be used as an `{% include %}` in any website you want, in any layout you want. Want to see it in action? Here are some websites that I know of using this solution.

- [the docs.docker.com website](https://github.com/docker/docker.github.io/pull/1474)
- [the UK Ministry of Justice Technical Guidance site](https://github.com/ministryofjustice/technical-guidance/pull/7)

For more information regarding how this include works, [read the blog post](https://allejo.io/blog/a-jekyll-toc-in-liquid-only/).

## Usage

Alright, so how do you use it? In any given Jekyll layout, you have the `content` variable, which has the HTML rendered from the markdown source.

1. Download the latest `toc.html` file
2. Toss that file in your `_includes` folder
3. Use it in your Liquid

   ```liquid
   {% include toc.html html=content %}
   ```

## Parameters

This snippet is highly customizable. Here are the available parameters to change the behavior of the snippet.

| Parameter  |  Type  | Default | Description |
| ---------  | :----: | :-----: | ----------- |
| `html`     | string | <sup>*</sup> | the HTML of compiled markdown generated by kramdown in Jekyll |
| `sanitize` | bool   | false  | when set to true, the headers will be stripped of any HTML in the TOC |
| `class`    | string | ''     | a CSS class assigned to the TOC; concat multiple classes with '.' |
| `id`       | string | ''     | an ID to assigned to the TOC |
| `h_min`    | int    | 1      | the minimum TOC header level to use; any heading lower than this value will be ignored |
| `h_max`    | int    | 6      | the maximum TOC header level to use; any heading greater than this value will be ignored |

<sup>*</sup> This is a required parameter

## License

This snippet may be redistributed under either the [BSD-3](https://github.com/allejo/jekyll-toc/blob/master/LICENSE.BSD3.md) or [MIT](https://github.com/allejo/jekyll-toc/blob/master/LICENSE.MIT.md) licenses.
