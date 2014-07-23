openlibrary-utils
=================

The suite of programs retrieves bibliographic data and Open Library pages for a set of identified books, organizes these for selection based on quality, and makes appropriate changes to the MARC records based on the library's requirements. In addition, statistics about book downloads are obtained via simple integration with the bit.ly URL shortening service.

## Files

### /src

**olpublicdomain.py**

This program takes a TSV spreadsheet of authors/titles and searches OpenLibrary for the best matching record with full-text available on the Internet Archive, returning a TSV sheet of likely candidate eBooks.

* input: ../data/SCCL-classics-ebook-candidates.tsv
* output: ../data/SCCL-classics-edition-author-work.tsv


**olmarcdecorator.py**

This program takes a TSV spreadsheet of OpenLibrary URLs that have corresponding ePub files on Internet Archive, retrieves the Internet Archive MARC record data, and inserts that data into a MRC file.

* input: ../data/SCCL classics candidates - v3 selected.tsv
* output: ../data/SCCLclassics.mrc


**downloadstats.py**

This program takes a list of bit.ly URLs and retrieves monthly statistics of click-throughs.

* input: ../data/SCCL-classic-eBooks-URLs-all.tsv
* output: *<stdout>*

**iaabbyqa.py**

This program analyzes XML OCR results to determine OCR confidence statistics.

* input: TBD
* output: TBD


For more information, contact team@galecia.com.



