# HugoModo Image Processing

Image Processing for Hugo sites.

## Shim

HugoModo Image Processing includes a collection of shims for providing the same image processing treatment to markdown in your site's content.

To activate it, create a file in your Hugo site at `data/config/imageProcessing.toml` with the content:

``` toml
contentShim = true
```

This will break other shortcodes on your site, so you may also want to install [HugoModo Shortcode Partials](https://github.com/hugomodo/hugomodo-shortcode-partials), which contains shims to fix some of the shortcodes.
