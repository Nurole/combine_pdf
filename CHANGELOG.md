#Change Log

***

Change log v.0.1.11

**fix**: fixed a bug where Page Resources and ColorSpace data wouldn't be inherited correctly from the Catalog and Pages parent objects. This issue could cause pages to render without all their content intact. This issue is now fixed (although more testing should be done for multiple inheritance).

**?fix?** Attempted to fix [the issue reported by srogers](https://github.com/boazsegev/combine_pdf/issues/10), by forcing all String byte collections to return an Array. waiting confirmation for fix (couldn't reproduce the issue just yet, as I can't seem to install Ruby MRI 1.9.3 on my mac).

***

Change log v.0.1.10

**fix**: fixed a typo that prevented access to the CombinePDF::VERSION constant.

***

Change log v.0.1.9

**fix**: possible fix for bug reported by lamphuongha, regarding PDF 1.5 streams. I await confirmation that the fix actually works, as I cannot seem to reproduce the whole spectrum of the bug on my system...

***

Change log v.0.1.8

**fix**: Fixed an [issue reported by Saba](https://github.com/boazsegev/combine_pdf/issues/8), where PDF files that were written using bad practices (namely, without wrapping their content streams correctly) would not be stamped correctly due to changes in the space matrix (CTM). Fixed by wrapping all existing streams before stamping.

***

Change log v.0.1.7

**fix**: PDF `insert` had a typo in the code that would cause failure when unsupported object insertion was attempted - fixed by Nathan Keyes (nkeyes).

***

Change log v.0.1.6

**fix**: added Mutex to font library (which was shared by all PDFWriter objects) - now fonts are thread safe (PDF objects are NOT thread safe by design).

**fix**: RTL recognition did not reverse brackets, it should now correctly perform brackets reversal for any of the following: (,),[,],{,},<,>.

**update**: updated license to MIT.

**known issues**: encrypted PDF files can sometimes silently fail (producing empty pages) - this is because on an attempted decrypt. more work should be done to support encrypted PDF files. please feel fee to help.

I use this version on production, where I have control over the PDF files I use. It is beter then system calls to pdftk (which can cause all threads in ruby to hold, effectively causing my web app to hang).