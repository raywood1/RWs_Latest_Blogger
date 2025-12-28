---
layout: post
title: "Registry Edit to Let Excel 2003 Read Quattro Files"
date: 2008-05-19
---

<div class="post-body">
<p>After much screwing around with <a href="https://web.archive.org/web/20190906053838/http://support.microsoft.com/kb/922848/">the Microsoft advice</a> and reading of <a href="//web.archive.org/web/20190906053838/https://www.google.com/search?aq=f&amp;num=100&amp;hl=en&amp;newwindow=1&amp;rlz=1B3GGGL_enUS247US248&amp;q=%22HKEY_CURRENT_USER%5CSoftware%5CPolicies%5CMicrosoft%5COffice%5C11.0%5CExcel%5CSecurity%22&amp;btnG=Search">other postings</a>, here are the contents of the REG file I created that now allows me to read old Quattro and Lotus (e.g., WKS, WK1, WQ1) files with Excel 2003, after getting an error message reading, "You are attempting to open a file that is blocked by your registry policy setting":
<blockquote>Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Excel\Security\FileOpenBlock]
"LotusandQuattroFiles"=dword:00000000
"LegacyBinaryFiles"=dword:00000000
"LegacyDatabaseAndDatasourceFiles"=dword:00000000

[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Excel\Security\FileSaveBlock]
"LotusandQuattroFiles"=dword:00000000
"LegacyBinaryFiles"=dword:00000000
"LegacyDatabaseAndDatasourceFiles"=dword:00000000
</blockquote>Note:  in case it wraps oddly in your browser, each opening quotation mark begins a new line, as does each opening bracket.  You also need the title line.

To make it work, copy and paste those lines verbatim into a Notepad file.  Save it in Unicode formatting to a file called "Enable Excel to Read Quattro Files.reg".  Close it.  Double-click on it and run it.

Same basic instructions for another REG file I have here, which I have named "Enable Excel to Open Old Spreadsheets.reg".  I didn't have to run it today, but I believe the updating of Office 2003 with Service Pack 3 (?) did require it previously:
<blockquote>Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Common\OICEExemptions]
"ExemptDirectory"="E:\\Current\\Projects\\Computer and Data\\Old Data\\Old Spreadsheets"

</blockquote></p>
<div style="clear: both;"></div>
</div>

---
### Comments
**raywood**:
Let's try that again.  On my screen, at least, the long lines in the REG files are obscured.  It goes like this:For the first one:[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Excel\Security\FileOpenBlock]and[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Excel\Security\FileSaveBlock]For the second one:[HKEY_CURRENT_USER\Software\Microsoft\Office\11.0\Common\OICEExemptions]

