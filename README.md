Copyright 2020 The Khronos Group Inc.  
SPDX-License-Identifier: Apache-2.0

# reuse-error
Demonstrate a problem with REUSE 0.11.0 parsing a legal RTF file

The file 'License.rtf' originally comes from https://github.com/KhronosGroup/KTX-Software/commit/36176c273322f13e656e5da433b059debc8b9f21 . In order to show a problem with REUSE, I've created this otherwise empty repository. Running 'reuse lint' on this repository generates

```
reuse._util - ERROR - Could not parse 'Apache-2.0\'
reuse.report - ERROR - Unexpected error occurred while parsing 'cmake/License.rtf'
KeyError: 'path'
# READ ERRORS

Could not read:
* cmake/License.rtf
```

However, the license information is entered in License.rtf and looks correct when viewing it in e.g. Libreoffice. While it's understandable that the REUSE tool would not read every possible documentation format, having it throw an error attempting to read .rtf suggests an underlying problem in whatever component consumes this type of file.
