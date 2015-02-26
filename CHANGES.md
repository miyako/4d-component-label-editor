2015-02-26
---

**New**:```boolean $success := LABEL_Convert_document (->blob|text $label{; boolean $withPrintSettings})``` 

* usage:

a. takes a path to a .4LB document, on success, returns the 4LBX (XML) in text.

b. takes a BLOB .4LB document, on success, return the 4LBX (XML) in BLOB.

optionally you can specify whether to include the print settings structure by setting $withPrintSettings to true. by default,  the information is excluded (it is not very useful and only increases the XML size). not very useful, in the sense that you would probably want to use regular 4D command to control the print settings.

**Modified**: ```LABEL_OPEN_EDITOR```

you can now pass a 4LBX (XML) text instead of path. 

**Fixed**: virtual structure support
