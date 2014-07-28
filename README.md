openlibrary-utils
=================

The suite of programs retrieves bibliographic data and Open Library pages for a set of identified books, organizes these for selection based on quality, and makes appropriate changes to the MARC records based on the library's requirements. In addition, statistics about book downloads are obtained via simple integration with the bit.ly URL shortening service.

This project was supported by a Library Services and Technology Act (LSTA) granted to Santa Clara County Library District (SCCLD) from the California State Library to fund the exploration of the effect of including public domain e-books in the library's catalog for discovery by users, and to observe whether e-book use would increase for the selected books. The project was conducted between July 2013 and June 2014.

## Documentation & Resources

### Requirements

* python 2
* python modules:
  * requests
  * simplejson
  * pymarc
  * requests-cache
  * elementtree


1. Prepare list of candidate books.
  * Create new spreadsheet with two columns, TITLE and AUTHOR, respectively.
  * Populate the spreadsheet with potential e-Books that you're searching for.
  * Save as ../data/candidate_seed.tsv (tab-separated text file).
2. Run olpublicdomain.py (within /src/ folder) to create a list of matching OpenLibrary records.
  * The /data/ folder should now contain a file called olpd_out.tsv containing the official author record, title record, publication date, and OpenLibrary URL for each work.
  * The /cache/ folder should now contain XML records for each matching record, which will later allow the highest-quality version of each work to be selected based on OCR quality analysis (depends on completion of iaabbyqa.py program).
3. Edit the olpd_out.tsv file to include only the specific OL editions you wish to include in your catalog.
4. TBD
5.



* View librarian-centric documentation here:

http://htmlpreview.github.io/?https://github.com/galecia/openlibrary-utils/blob/master/docs/librarians.html


## Files

### /src

**olpublicdomain.py**

This program takes a TSV spreadsheet of authors/titles and searches OpenLibrary for the best matching record with full-text available on the Internet Archive, returning a TSV sheet of likely candidate e-books.

* input: ../data/candidate_seed.tsv
* output: ../data/olpd_out.tsv


**olmarcdecorator.py**

This program takes a TSV spreadsheet of OpenLibrary URLs that have corresponding ePub files on Internet Archive, retrieves the Internet Archive MARC record data, and inserts that data into a MRC file.  In addition, e-book resource URLs are shortened using bit.ly for later statistical analysis.

* input:
  * ../data/openlib_url_list.tsv
  * ../data/ebooks.mrc
* output: updated ebooks.mrc file


**downloadstats.py**

This program takes a list of bit.ly URLs and retrieves monthly statistics of click-throughs.

* input: ../data/ebook_url_list.tsv
* output: *console: stdout*  (append ">> filename.tsv" to command to save)


**iaabbyqa.py**

This program analyzes XML OCR results to determine OCR confidence statistics.  _This program is incomplete._

* input: a ../cache/ folder containing XML record results output by _olpublicdomain.py_
* output: TBD

### Other

**bitly_credentials.txt**

To use the bit.ly analytics functionality, you'll need to create a bit.ly account and enter your API credentials in this file in the following format:

_bitly login_
_bitly API key_
_bitly access token_



For more information, contact team@galecia.com.
