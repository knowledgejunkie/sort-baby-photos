sort-baby-photos
================


Status
------

sort-baby-photos is a work in progress.


Introduction
------------

sort-baby-photos is a Perl script that organises your baby (or any other)
photos.

sort-baby-photos organises your photos into a directory hierarchy with naming
relative to a given start date (e.g. "00y/03m", "02y/11m"). For organising baby
photos, this date will usually be the baby's date of birth.

sort-baby-photos extracts EXIF data from each photo it processes to determine
when it was taken (via the DateTimeOriginal tag).

Unlike other great photo management tools such as
[SortPhotos](https://github.com/andrewning/sortphotos) that organise your
photos into directories with naming based on the date the photo was taken (e.g.
year/month or year/month/day), the use of a directory naming system based on
your baby's "age" makes it very easy to quickly see all photos taken in each
month (or year, etc) since birth.

This makes using sort-baby-photos ideal for choosing photos for baby photobooks.


Prerequisites
-------------

sort-baby-photos requires the following Perl modules to be installed:

- DateTime;
- DateTime::Duration;
- File::Find;
- File::Path
- Image::ExifTool

If sort-baby-photos should fail to run due to missing dependencies, please
install them via your favourite package manager or from CPAN.


Usage
-----

To sort photos in a given directory into a new output directory structure,
based on a given starting date:

    ./sort-baby-photos --input-dir=~/Photos --output-dir=~/Sorted_Photos --start-date=2015-12-07 [--symlink]

- start-date should be given in ISO 8601 format e.g. YYYY-MM-DD (date only) or
  YYYY-MM-DDThh:mm:ss (date and time).

License
-------

Copyright (c) Nick Morrott

Licensed under the [GNU GPL v2 or later](http://www.gnu.org/licenses/gpl.html).
