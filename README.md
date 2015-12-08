sort-baby-photos
================


Status
------

sort-baby-photos is a work in progress.


Introduction
------------

sort-baby-photos is a script that organises your baby (or any other) photos. It
is written in Perl.

sort-baby-photos organises your photos into a directory hierarchy with naming
relative to a given start date (e.g. "~/Sorted/00y/03m", "~/Sorted/02y/11m").
For organising baby photos, this date will usually be the baby's date of birth.

sort-baby-photos extracts the Exif data from each photo it processes to determine
when it was taken (via the DateTimeOriginal tag).

Unlike other great photo management tools such as
[SortPhotos](https://github.com/andrewning/sortphotos) that organise your
photos into directories with naming based on the date the photo was taken (e.g.
year/month or year/month/day), the use of a directory hierarchy based on your
baby's "age" makes it very easy to quickly see all photos taken in each month
(or year, etc) since birth.

This makes using sort-baby-photos ideal for choosing photos for photobooks.


Prerequisites
-------------

sort-baby-photos uses the following non-core Perl modules:

- DateTime
- DateTime::Duration
- DateTime::Format::ISO8601
- Image::ExifTool

If sort-baby-photos should fail to run due to missing dependencies, please
install them via your favourite package manager or from CPAN.

On Debian/Ubuntu, the following should install the necessary dependencies:

    # apt-get install libdatetime-format-iso8601-perl libimage-exiftool-perl


Usage
-----

To sort photos in a given directory into a new output directory hierarchy,
based on a given starting date:

    $ ./sort-baby-photos --input-dir=~/Unsorted_Photos --output-dir=~/Sorted_Photos --start-date=2015-12-07 [--symlink] [--debug]

- *--input-dir* and *--output-dir* paths can be given in relative or absolute
  format. All paths are converted to absolute paths internally.
- *--start-date* should be given in ISO 8601 format e.g. YYYY-MM-DD (date only)
  or YYYY-MM-DDThh:mm:ss (date and time).
- If *--symlink* is specified sort-baby-photos will attempt to create symlinks
  from the original photos to the output directory hierarchy. By default,
  sort-baby-photos will move photos into the output directory hierarchy.
- *--debug* will provide additional debugging output during processing.

License
-------

Copyright (c) Nick Morrott

Licensed under the [GNU GPL v2 or later](http://www.gnu.org/licenses/gpl.html).
