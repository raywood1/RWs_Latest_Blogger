---
layout: post
title: "Excel 2003:  Print or Export the Formulas Used in Each Cell"
date: 2012-02-29
---

<div class="post-body">
<p>I had a spreadsheet in Excel 2003.  (I suspect the approach used here would also work in other versions of Excel, but I have not tried it.)  I wanted to print out the formulas used in each cell.  I did <a href="https://web.archive.org/web/20151125203733/https://www.google.com/search?q=Excel+%22export+formulas%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">a couple</a> of <a href="https://web.archive.org/web/20151125203733/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=JnL&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=%22export+formulas+from+Excel%22&amp;oq=%22export+formulas+from+Excel%22&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=15869l18707l0l19194l12l10l0l0l0l3l338l1219l3.6.0.1l10l0" target="_blank">searches</a> and wound up in <a href="https://web.archive.org/web/20151125203733/http://www.pcreview.co.uk/forums/do-you-print-showing-formulas-excel-2000-a-t2428644.html" target="_blank">a thread</a> where they were advising me to use a macro for this purpose.  The steps I used to set up the macro were similar to those that I had used for <a href="https://web.archive.org/web/20151125203733/http://raywoodcockslatest.blogspot.com/2011/04/finding-last-occurrence-of-character-in.html" target="_blank">another Excel macro</a>:<br/>
<ol><li>Close all Excel files other than the one you're working on.</li>
<li>Go into Tools &gt; Macro &gt; Visual Basic Editor &gt; Insert &gt; Module.</li>
<li>Copy and paste macro text (see below) into the window.</li>
<li>Go to File &gt; Close and return to Microsoft Excel.</li>
<li>In this case, I used the macro by going into Tools &gt; Macro &gt; Macros and running the ListFormulas macro.</li>
</ol>The text of the macro -- what I copied and pasted into the module window -- was as follows:<br/>
<blockquote><pre>Sub ListFormulas()
    Dim FormulaCells As Range, Cell As Range
    Dim FormulaSheet As Worksheet
    Dim Row As Integer
    
<span style="color: blue;">'   Create a Range object for all formula cells</span>
    On Error Resume Next
    Set FormulaCells = Range("A1").SpecialCells(xlFormulas, 23)
    
<span style="color: blue;">'   Exit if no formulas are found</span>
    If FormulaCells Is Nothing Then
        MsgBox "No Formulas."
        Exit Sub
    End If
    
<span style="color: blue;">'   Add a new worksheet</span>
    Application.ScreenUpdating = False
    Set FormulaSheet = ActiveWorkbook.Worksheets.Add
    FormulaSheet.Name = "Formulas in " &amp; FormulaCells.Parent.Name
    

<span style="color: blue;">'   Set up the column headings</span>
    With FormulaSheet
        Range("A1") = "Address"
        Range("B1") = "Formula"
        Range("C1") = "Value"

        Range("A1:C1").Font.Bold = True
    End With
    
<span style="color: blue;">'   Process each formula</span>
    Row = 2
    For Each Cell In FormulaCells
        Application.StatusBar = Format((Row - 1) / FormulaCells.Count, "0%")
        With FormulaSheet
            Cells(Row, 1) = Cell.Address _
                (RowAbsolute:=False, ColumnAbsolute:=False)
            Cells(Row, 2) = " " &amp; Cell.Formula
            Cells(Row, 3) = Cell.Value
            Row = Row + 1
        End With
    Next Cell
    
<span style="color: blue;">'   Adjust column widths</span>
    FormulaSheet.Columns("A:C").AutoFit
    Application.StatusBar = False
End Sub </pre></blockquote>(Note that the format of this blog may wrap some lines.  Copying and pasting may yield better results than retyping.)  The author named in that code, <a href="https://web.archive.org/web/20151125203733/http://spreadsheetpage.com/index.php/book/excel_vba_programming_for_dummies2/">John Walkenbach</a>, provided <a href="https://web.archive.org/web/20151125203733/http://spreadsheetpage.com/index.php/tip/creating_a_list_of_formulas/" target="_blank">this code</a> and also offered a <a href="https://web.archive.org/web/20151125203733/http://spreadsheetpage.com/index.php/pup/" target="_blank">Power Utility Pak</a> ($40) that contained this and other tools.  I had installed a couple of freeware utility collections -- <a href="https://web.archive.org/web/20151125203733/https://www.google.com/search?q=%22ASAP+Utilities%22&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">ASAP Utilities</a> and <a href="https://web.archive.org/web/20151125203733/https://www.google.com/search?q=Morefunc&amp;ie=utf-8&amp;oe=utf-8&amp;aq=t&amp;rls=org.mozilla:en-US:official&amp;client=firefox-a" target="_blank">Morefunc</a> -- and I hardly ever used them.  I checked <a href="https://web.archive.org/web/20151125203733/http://www.asap-utilities.com/asap-utilities-excel-tools-hierarchical-list.php?lang=en_us" target="_blank">the list</a> of tools in ASAP Utilities, just in case, but didn't find anything quite along these lines.  <a href="https://web.archive.org/web/20151125203733/https://www.google.com/search?num=50&amp;hl=en&amp;newwindow=1&amp;client=firefox-a&amp;hs=mvg&amp;rls=org.mozilla%3Aen-US%3Aofficial&amp;q=Morefunc+list+formulas&amp;oq=Morefunc+list+formulas&amp;aq=f&amp;aqi=&amp;aql=&amp;gs_sm=3&amp;gs_upl=158349l160000l0l160151l14l13l0l0l0l0l188l900l8.4l12l0" target="_blank">A quick glance</a> revealed no list of Morefunc utilities.<br/>
<br/>
When I ran the macro (step 5, above), it seemed to hang my machine.  I was using a fairly large spreadsheet -- I probably should have tried it on something smaller -- but instead I went to bed.  I didn't know how long it took, but it worked.  When I awoke, it had created a new worksheet (i.e., a new tab at the bottom of the spreadsheet), with three columns:  Address (e.g., F2), Formula (e.g., =C2), and Value (e.g., 17).</p>
<div style="clear: both;"></div>
</div>

---
### Comments
**Anonymous**:
Thanks for this, it did exactly what I needed!John

