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

Demo
----
Visit http://new.lucubration.com/articles/how-hot-wire-shapes-foam for a
working example. The images on this page were uploaded full-size and then
configured to use a half-size Scale&Crop filter upon display. Combined with
Lightbox2, this provides for an easy re-scaling effect.

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

4. Browse to /admin/config/content/formats and configure each input format that
   you want the filter to run against. When you enable the filter, be sure it
   runs BEFORE any filters that correct or block HTML tags, and that any filters
   that block tags are configured to allow IMG tags in the output.
   
Classes to Styles has a set of its own options that you should review before
clicking Save. Help descriptions are provided. For reference, here are the
settings in use on the author's site:
   
    Class List:
    wysi-1=wysi_1
    wysi-2=wysi_2
    Link to Original File: Checked
    Additional IMG classes: lightbox
    IMG REL tag: <not set>
    Link Classes: original
     
Usage
-----
Usage is simple. When embedding an image in a WYSIWYG field, just select one of
the classes you defined above to apply to the image. The author uses IMCE
for file selection, but any module would work as long as you can apply a class
to the image.

When viewing the page, Classes to Styles will reformat IMG URLs so they use
Drupal's Image Styles facility to reformat and then cache the files on the
server. If you have enabled linking to the original file, a link will be wrapped
around the image to allow the user to view the original file.

If you use Lightbox2, this dovetails nicely into the setting called
"Custom Class Images" at /admin/config/user-interface/lightbox2/automatic.
Just enable this handler (the author uses "Lightbox grouped") and add the class
used above ("lightbox") to the "Custom image trigger classes" setting.
