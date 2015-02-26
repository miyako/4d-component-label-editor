2015-02-26
---

**New**:```picture $preview := LABEL_Get_document_preview (->blob|text $label)```

* usage:

a. takes a path to a .4LB document, on success, returns its image as picture.

b. takes a BLOB .4LB document, on success, return its image as picture.

c. take a .4LBX as text, on success, return its image as picture.

d. takes a path to a .4LBX document, on success, returns its image as picture.

**New**:```boolean $success := LABEL_Convert_document (->blob|text $label{; boolean $withPrintSettings})``` 

* usage:

a. takes a path to a .4LB document, on success, returns the 4LBX (XML) as text.

b. takes a BLOB .4LB document, on success, return the 4LBX (XML) as BLOB.

optionally you can specify whether to include the print settings structure by setting $withPrintSettings to true. by default,  the information is excluded (it is not very useful and only increases the XML size). not very useful, in the sense that you would probably want to use regular 4D command to control the print settings.

**Modified**: ```LABEL_OPEN_EDITOR (->table{; blob|text $labelIn{; ->blob|text $labelOut}})```

you can now pass a 4LBX (XML) text instead of path. 

optionally you can receive the new .4LBX (XML) if the editor dialog was accepted.

**Modified**: ```LABEL_PRINT_SELECTION```

you can now pass a 4LBX (XML) text instead of path. 

**Fixed**: virtual structure support

**Fixed**: memory leak in ```LABEL_PRINT_SELECTION```

