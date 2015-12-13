sort-baby-photos
================


Status
------

sort-baby-photos is a work in progress nearing completion.


Introduction
------------

sort-baby-photos organises your baby photos into nested directories for each
month since birth. This makes using sort-baby-photos ideal for choosing photos
for regular photobooks.

sort-baby-photos organises photos into an output directory hierarchy with
directory naming relative to a specified start date.  For organising baby
photos, this date will usually be the baby's date of birth.

Under the top-level output directory, the first level of sub-directories
represent the age of the baby in years (e.g. ./01y).

Each of these 'year' sub-directories may contain up to 12 'month'
sub-directories (00m-11m), which are where the photos are located after
processing.

So, a top-level output directory containing the path ./01y/06m will contain all
photos processed that were taken at least 1 year and 6 months and less than
1 year and 7 months after the specified start (birth) date

sort-baby-photos extracts Exif metadata from each photo it processes to
determine when it was taken (via the DateTimeOriginal tag).

Unlike other photo management tools such as
[SortPhotos](https://github.com/andrewning/sortphotos) that organise photos
into directories with naming based on the date the *photo* was taken (e.g.
year/month or year/month/day), the use of a directory hierarchy based on your
*baby's age* makes it very easy to quickly see all photos taken in each
non-calendar month (or year, etc) since birth.



Prerequisites
-------------

sort-baby-photos uses a few popular non-core Perl modules:

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

To sort photos in a given input directory into a new output directory hierarchy,
based on a given starting date (e.g. 2015-12-07), run:

    $ ./sort-baby-photos --input-dir=~/Unsorted_Photos --output-dir=~/Sorted_Photos --start-date=2015-12-07 [--date-prefix] [--recursive] [--move | --symlink]

modifying imput and output directories as necessary.

- *--input-dir* and *--output-dir* can be given as either relative or absolute
  paths. All paths are converted to absolute paths internally.
- *--start-date* should be given in ISO 8601 format e.g. YYYY-MM-DD (date only)
  or YYYY-MM-DDThh:mm:ss (date and time).
- If *--date-prefix* is specified sort-baby-photos will prepend a timestamp
  (currently seconds since the Unix epoch) to each filename when moving or
  creating a symlink.  This allows natural sorting of files in the output
  directory hierarchy based on the date the photo was taken, rather than the
  original filename of the photo, and should help ensure photos are listed in
  chronological order within each output directory.
- If *--recursive* is specified, sort-baby-photos will search for all photos
  available in the given input directory and additionally in any directories
  within the input directory. By default, only photos found in the input
  directory itself are processed.
- If *--move* is specified sort-baby-photos will move photos from the input
  directory to the output directory hierarchy. This is the default behaviour if
  neither *--move* nor *--symlink* options are given.
- If *--symlink* is specified sort-baby-photos will create a symlink from the
  input directory to the output directory hierarchy for each processed photo.
- *--quiet* will not print progress messages during processing.
- *--verbose* will provide additional progress messages during processing.
- *--help* will print an informative help message
- *--man* will print the full manual
- *--version* will print the current version

Note that both short and long option names are supported - please read the help
or manual page for full details.


TODO
----

- Check for duplicate files in output directories
- Decide on default move/symlink behaviour
- File manager before/after screenshot

- Do we need a *--copy* option?
- Move and rename files to output directories and symlink them back into input
  directory with original filename?

License
-------

Copyright (c) Nick Morrott 2015

Licensed under the [GNU GPL v2 or later](http://www.gnu.org/licenses/gpl.html).
