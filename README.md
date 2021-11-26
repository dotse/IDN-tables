# IDN tables for .se and .nu

* [Overview](#overview)
* [IDN table files](#idn-table-files)
* [Primary source (DOCX) tables](#primary-source-docx-tables)
  * [Update the primary source tables](#update-the-primary-source-tables)
* [PDF table files]
  * [Create the PDF table files](#create-the-pdf-table-files)
* [XML table files](#xml-table-files)
  * [Available XML file](#available-xml-file)
  * [Update the XML table files](#update-the-xml-table-files)
  * [Upload updted XML file to IANA](#upload-updted-xml-file-to-iana)

## Overview

The IDN tables are available in this repository for updates. To
do the updates you have to follow the normal git procedures. 

Some of the files (PDF and XML) are automatically available from 
Github pages, in this case https://dotse.github.io/IDN-tables/. 
Only the files in the [docs] folder in this repository are 
available from Github pages.

When a file in the [docs] folder is updated, it will
automatically be updated in Github pages. This is, however, limited
to the "master" branch, which is the only branch at the time of
writing.

## IDN table files

In this repository the .se and .nu IDN tables appear in three
types of files:

* DOCX (primarily Microsoft Word format)
* PDF
* XML

These are described below.

## Primary source (DOCX) tables

The primary source of the IDN tables are the DOCX files. They are
are stored at the top level in this repository and are the following
files:

* [IDN_table_nu.docx]
* [IDN_table_se.docx]

If anything should be changed in the IDN table proper, then it must
be started by updating these primary source files.

### Update the primary source tables

1. Make sure that you do not change the file name or move the file
   to a new place in this directory.
2. Make sure that you always update the revision and date of the
   table file in the very bottom of the file.
   1. Always update revision and date even if the change is minor.
   2. If the revision says "C" then the next revision is "D". If the
      revison is "Z" then the next revision is "AA".
   3. The date should be the date when the revsion is completed.
3. When the update is completed, go to the [PDF file section][PDF table files]
   in this document.
4. If there is any change in the code point repertoire or the
   contextual rules (restrictions) then the XML files must also be
   updated.

## PDF table files

The PDF files are generated from the DOCX source files. Usually
you can use print or export function to generate the PDF file.
Make sure you create an PDF/A type of PDF file for maximal
compatability.

### Create the PDF table files

1. Make sure you keep the same name of the PDF file as the previous
   version, or else the [permalinks][permalink] to the PDF table
   files will not work.
2. The PDF files must be put into the [docs] folder.

## XML table files

The XML table files are also called LGR table files. If any
update has been done to the code point repertoire or the
contextual rules (restrictions) in the primary source table
then the XML (LGR) file or files must also be updated.

You should be familiar with the LGR specification ([RFC 7940])
when you update the XML files.

The XML (LGR) files could be tested and verified with the
following tool:
* [ICANN LGR Tool]

### Available XML file

For .nu there is one XML file in the [docs] folder:
* [nu_Latin_script.xml]

For .se there are two XML files in the [docs] folder:
* [se_Latin_script.xml] for the Latin script part of the .se IDN 
  table
* [se_Yiddish_language.xml] for the Yiddish language part of the
  .se IDN table

### Update the XML table files

1. Make sure that the update match the primary source file.
2. The "\<version\>" field must be incremented to the next higher 
   integer. The same integer should be set to "Table Version" 
   in the decription field.
3. The "\<date\>" and "\<validity-start\>" fields should have the
   date of the update and the date of the update of primary 
   source, respectively. The latter does not have to be updated
   unless there is an effective change.
3. In the description field, "Table date" should match "\<date\>"
   and "Normative Date" the date of the primary source file.
4. In the decription field, "Normative Version" should match
   the version of the primary source.
5. In case of the XML files for .se, if one is update, always
   update the other to keep the same "\<version\>".
6. Always validate the updated XML file with e.g. `xmllint`
   against the LGR schema file [lgr.rng].
   
### Upload updted XML file to IANA

If any of the XML files have been updated, then it should be
uploaded to the IANA 
[IDN tables repository][IANA IDN tables repository]. The file
name is then expected to include the version integer.

1. Open the XML file and take note of the version integer in the
   "\<version\>" field. Close the file.
2. Make a copy of the file to somewhere outside the reposiftory. 
3. If the version integer is "9" then add "_9" before ".xml". If 
   the version integer is "9" for all XML files, then the new 
   names of the copied files will be:
   * nu_Latin_script_9.xml
   * se_Latin_script_9.xml
   * se_Yiddish_language_9.xml
4. Do not change the name of the files in this repository.


[IANA IDN tables repository]: https://www.iana.org/domains/idn-tables
[ICANN LGR Tool]:             https://lgrtool.icann.org/
[IDN_table_nu.docx]:          IDN_table_nu.docx
[IDN_table_se.docx]:          IDN_table_se.docx
[PDF table files]:            #pdf-table-files
[RFC 7940]:                   https://tools.ietf.org/html/rfc7940
[docs]:                       docs
[lgr.rng]:                    schema/lgr.rng
[nu_Latin_script.xml]:        docs/nu_Latin_script.xml
[permalink]:                  https://en.wikipedia.org/wiki/Permalink
[se_Latin_script.xml]:        docs/se_Latin_script.xml
[se_Yiddish_language.xml]:    docs/se_Yiddish_language.xml

