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


1. Prepare list of candidate books
  * Create new spreadsheet
  * Populate two columns, TITLE and AUTHOR, respectively
  * Optionally, add a third column for WORK TITLE, that can contain collection or subtitle details (UNTESTED)
  * Save as ../data/candidate_seed.tsv (tab-separated text file)
2. Run olpublicdomain.py (within /src/ folder) to create a list of matching OpenLibrary records
  * The /data/ folder should now contain a file called olpd_out.tsv containing the official author record, title record, publication date, and OpenLibrary URL for each work.
  * The /cache/ folder should now contain XML records for each matching record, which will later allow the highest-quality version of each work to be selected based on OCR quality analysis
3. TBD
4. TBD
5.



* View librarian-centric documentation here:

http://htmlpreview.github.io/?https://github.com/galecia/openlibrary-utils/blob/master/docs/librarians.html


## Files

### /src

**olpublicdomain.py**

This program takes a TSV spreadsheet of authors/titles and searches OpenLibrary for the best matching record with full-text available on the Internet Archive, returning a TSV sheet of likely candidate eBooks.

* input: ../data/candidate_seed.tsv
* output: ../data/olpd_out.tsv


**iaabbyqa.py**

This program analyzes XML OCR results to determine OCR confidence statistics.

* input: a ../cache/ folder containing XML record results output by _olpublicdomain.py_
* output: TBD


**olmarcdecorator.py**

This program takes a TSV spreadsheet of OpenLibrary URLs that have corresponding ePub files on Internet Archive, retrieves the Internet Archive MARC record data, and inserts that data into a MRC file.

* input: ../data/openlib_url_list.tsv
* output: ../data/ebooks.mrc


**downloadstats.py**

This program takes a list of bit.ly URLs and retrieves monthly statistics of click-throughs.

* input: ../data/ebook_url_list.tsv
* output: *console: stdout*  (append ">> filename.tsv" to command to save)


For more information, contact team@galecia.com.
