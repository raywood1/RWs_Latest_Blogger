---
layout: post
title: "Optical Character Recognition Freeware:  JOCR and FreeOCR"
date: 2012-03-10
---

<div class="post-body">
<p>I had some PNG images of text files.  I wanted to do optical character recognition (OCR) to convert their contents into text.<br/>
<br/>
I already had Adobe Acrobat.  I tried printing the PNGs as PDFs in Acrobat, which was capable of doing OCR.  Unfortunately, its recognition was poor, even when I set its PDF printer to 1200 DPI.<br/>
<br/>
Next, I turned to <a href="https://web.archive.org/web/20120701030920/http://www.freewaregenius.com/2011/11/01/how-to-extract-text-from-images-a-comparison-of-free-ocr-tools/#cuneiformopenocr" target="_blank">a fairly recent review</a> of desktop OCR software.  It looked like the best-known OCR freeware engines might be the Cuneiform, the Tesseract, and the SimpleOCR.  I checked Softpedia for examples of those.  <a href="https://web.archive.org/web/20120701030920/http://www.softpedia.com/get/Office-tools/Other-Office-Tools/CuneiForm.shtml" target="_blank">Cuneiform</a> was virtually unknown, and <a href="https://web.archive.org/web/20120701030920/http://www.softpedia.com/get/Office-tools/Text-editors/SimpleOCR.shtml" target="_blank">SimpleOCR</a> was making a mediocre showing, but <a href="https://web.archive.org/web/20120701030920/http://www.softpedia.com/get/Others/Miscellaneous/FreeOCR.shtml" target="_blank">FreeOCR</a> (using Tesseract) seemed relatively popular.<br/>
<br/>
That review also directed me toward <a href="https://web.archive.org/web/20120701030920/http://www.freewaregenius.com/2007/03/08/jocr/" target="_blank">JOCR</a>, which was apparently designed to do OCR directly from the screen.  The reviews of JOCR at <a href="https://web.archive.org/web/20120701030920/http://download.cnet.com/JOCR/3000-2192_4-10768898.html?tag=contentMain;contentBody;1d" target="_blank">CNET</a> and <a href="https://web.archive.org/web/20120701030920/http://www.softpedia.com/get/Multimedia/Graphic/Graphic-Capture/JOCR.shtml" target="_blank">Softpedia</a> were underwhelming.  But because it was supposedly designed to do OCR directly from the screen, I decided to compare it against one of the others.  FreeOCR seemed to be the most likely candidate.  I might have gotten different results from one of the other OCR engines, or from another implementation of the Tesseract engine.<br/>
<br/>
I let JOCR and FreeOCR try their luck with a screenshot taken from a maximized Notepad display of a text file, upsampled to 300 DPI.  (FreeOCR had frozen with a 600 DPI file, which JOCR had been able to handle without difficulty.)<br/>
<br/>
Briefly, the FreeOCR output was visibly inferior to the JOCR output.  Of course, this was a test with text from an image, for which JOCR was specially designed.  There was no question, at least within the parameters of this brief test, that JOCR was producing better output.<br/>
<br/>
Compared against the original text, the primary problem with the JOCR output was in the area of capitalization.  The recognized text was generally pretty accurate, with few dropped letters or other errors.  Overall, its output would have made a bad impression, if pasted directly into the body of a professional letter or memorandum; but its output was quite good for archival purposes of capturing the wording in an image.</p>
<div style="clear: both;"></div>
</div>

---
### Comments
