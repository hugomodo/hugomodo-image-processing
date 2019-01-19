# HugoModo Image Processing

Image Processing for Hugo sites.

## Shim

HugoModo Image Processing includes a collection of shims for providing the same image processing treatment to markdown in your site's content.

To activate it, create a file in your Hugo site at `data/config/imageProcessing.toml` with the content:

``` toml
contentShim = true
```

This will break other shortcodes on your site, so you may also want to install [HugoModo Shortcode Partials](https://github.com/hugomodo/hugomodo-shortcode-partials), which contains shims to fix some of the shortcodes.

## Support on Patreon
[![Patreon](https://c5.patreon.com/external/logo/become_a_patron_button.png)](https://www.patreon.com/bePatron?u=4780882)

## Support on Beerpay
Hey dude! Help me out for a couple of :beers:!

[![Beerpay](https://beerpay.io/hugomodo/hugomodo-image-processing/badge.svg?style=beer-square)](https://beerpay.io/hugomodo/hugomodo-image-processing)  [![Beerpay](https://beerpay.io/hugomodo/hugomodo-image-processing/make-wish.svg?style=flat-square)](https://beerpay.io/hugomodo/hugomodo-image-processing?focus=wish)

## Description

### Features

- Provides `imgproc` and `figproc` shortcodes for image processing in your content files.
- Uses `srcset` to load responsive image sizes on different screen resolutions.
- Can be configured to use Page Bundles, a headless Resources bundle, or both!

#### Todo

1. Equivalents for theme layouts are provided: `image-processing/imgproc.html` and `image-processing/figproc.html`.
  - These already exist. Modification required so that context can be passed.
2. Option to override existing `figure` shortcode.
3. Additional `imgcrop` shortcode using `.Fill` image processing function to crop images to given dimensions.
4. Potentially an `imgfit` shortcode as well, using `.Fit`. Could be useful for masonry layouts.
5. Support for featured and thumbnail images in page frontmatter and site config.
6. Support for opengraph and other meta tag images to be resized appropriately.
7. Support for `sizes` attribute alongside `srcset`; allow this to be altered in config.
8. Consider having minSize and maxSize settings in config and per proc.
  - Allowing these to be set where used will help to reduce repo bloat.
9. Add support for social and search graph image resizing.
  - opengraph
  - schema
  - twitter cards
  - structured data

## Installation

From your Hugo site's root directory:

*Recommended*

``` bash
git submodule add https://github.com/hugomodo/hugomodo-image-processing.git themes/hugomodo-image-processing
```

Or:

``` bash
cd themes
git clone https://github.com/hugomodo/hugomodo-image-processing.git
```

Then add `hugomodo-image-processing` to your site's themes in `config.toml`. Because it is considered an extension, it should be listed above any other HugoModo themes:

``` toml
themes = [
  "hugomodo-image-processing",
  ...
]
```

## Configuration

HugoModo Image Processing can be configured one of two ways. The default is to use Hugo's Page Bundles, but an alternative approach using an uploads directory that provides compatibility with third party Content Management Systems can be setup with minimal configuration.

### Page Bundles

By default, HugoModo Image Processing uses Page Bundles as described by the Hugo docs: [Page Bundles](https://gohugo.io/content-management/organization/#page-bundles)

No additional configuration is required to use HugoModo Image Processing this way.

### Uploads Directory

You can configure HugoModo Image Processing to use an uploads directory instead, for compatibility with some Content Management Systems such as Forestry who write up the idea behind the uploads directory here: [How To Use Hugo's Image Processing With Forestry](https://forestry.io/blog/how-to-use-hugo-s-image-processing-with-forestry/)

The HugoModo implementation is a little bit different, but fully compatible with Forestry at the time of writing.

To set it up add a file to your site at `data/imageProcessing/config.toml` with the following configuration:

``` toml
uploadsDir = "uploads"
```

...and that's it! You can now add your images to a `content/uploads` directory and have HugoModo's image processing shortcodes will look for your resources there instead.

### ...or both!

It is also possible to mix the two approaches. If the `src` string passed to imgproc contains a directory structure, it will look for your images in the given directory:

``` go-html-template
{{< imgproc src="/uploads/jakob-owens-212555-unsplash.jpg" >}}
```

## Shortcodes

### imgproc

``` go-html-template
{{< imgproc src="fabian-grohs-423591-unsplash.jpg" >}}
```

### figproc

``` go-html-template
{{< figproc src="fabian-grohs-423591-unsplash.jpg" caption="Computer on a desk" >}}
```
