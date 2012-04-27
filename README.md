Class Style Filter
==================

This Drupal module provides an input filter that allows WYSIWYG embedded images
to be restyled using Drupal's Image Styles functionality, rather than forcing
the content editor to upload scaled/cropped images. This also means design
decisions regarding thumbnail sizes for embedded files may be easily changed
later (by simply updating the image style) without having to re-edit existing
nodes.

It also provides some "glue" support for modules like Lightbox2. The module
can apply CLASS and REL tags to the image and/or a link wrapper to the original
file that Lightbox2 can use when displaying galleries.

Configuration
-------------
1. Download and enable this module.

2. Browse to /admin/config/content/wysiwyg and edit the settings for each
   WYSIWYG profile you want to support. Add classes that you can apply to
   images you want processed. The author's example site
   (http://www.lucubration.com/) uses the following "CSS -> CSS Classes" rule:

     Half-size WYSI=wysi-2
     Full-size WYSI=wysi-1

   Create one class for each image style you want to make.

3. Browse to /admin/config/media/image-styles and create image styles that the
   classes should be mapped to. On the author's site, there are two styles:

     wysi_1: Scale and Crop to 612x459 (this is a full-width image)
     wysi_2: Scale and Crop to 300x225 (this is a half-width image)

   Create one style that each image class will be translated into.

4. Browse to /admin/config/content/formats
