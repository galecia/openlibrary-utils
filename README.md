openlibrary-utils
=================

The suite of programs retrieves bibliographic data and Open Library pages for a set of identified books, organizes these for selection based on quality, and makes appropriate changes to the MARC records based on the library's requirements. In addition, statistics about book downloads are obtained via simple integration with the bit.ly URL shortening service.

## Documentation & Resources

### Requirements

* python 2
* python modules:
  * requests
  * simplejson
  * pymarc
  * requests-cache
  *


1. Prepare list of candidate books
  * Create new spreadsheet
  * Populate two columns: TITLE and AUTHOR (you do not need to create a header row)
  * Save as ../data/olpd_out.tsv (tab-separated text file)
2. Run olpublicdomain.py to create a list of matching OpenLibrary records
3. TBD
4. TBD
5.



* View librarian-centric documentation here:

http://htmlpreview.github.io/?https://github.com/galecia/openlibrary-utils/blob/master/docs/librarians.html


## Files

### /src

**olpublicdomain.py**

This program takes a TSV spreadsheet of authors/titles and searches OpenLibrary for the best matching record with full-text available on the Internet Archive, returning a TSV sheet of likely candidate eBooks.

* input: ../data/olpd_out.tsv
* output: ../data/candidate_seed.tsv


**olmarcdecorator.py**

This program takes a TSV spreadsheet of OpenLibrary URLs that have corresponding ePub files on Internet Archive, retrieves the Internet Archive MARC record data, and inserts that data into a MRC file.

* input: ../data/openlib_url_list.tsv
* output: ../data/ebooks.mrc


**downloadstats.py**

This program takes a list of bit.ly URLs and retrieves monthly statistics of click-throughs.

* input: ../data/ebook_url_list.tsv
* output: *console: stdout*  (append ">> filename.tsv" to command to save)

**iaabbyqa.py**

This program analyzes XML OCR results to determine OCR confidence statistics.

* input: TBD
* output: TBD


For more information, contact team@galecia.com.
