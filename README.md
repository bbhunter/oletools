python-oletools
===============
[![PyPI](https://img.shields.io/pypi/v/oletools.svg)](https://pypi.org/project/oletools/)
[![Build Status](https://travis-ci.org/decalage2/oletools.svg?branch=master)](https://travis-ci.org/decalage2/oletools)
[![Say Thanks!](https://img.shields.io/badge/Say%20Thanks-!-1EAEDB.svg)](https://saythanks.io/to/decalage2)

[oletools](http://www.decalage.info/python/oletools) is a package of python tools to analyze
[Microsoft OLE2 files](http://en.wikipedia.org/wiki/Compound_File_Binary_Format) 
(also called Structured Storage, Compound File Binary Format or Compound Document File Format), 
such as Microsoft Office 97-2003 documents, MSI files or Outlook messages, mainly for malware analysis, 
forensics and debugging. 
It is based on the [olefile](http://www.decalage.info/olefile) parser. 

It also provides tools to analyze RTF files and files based on the [OpenXML format](https://en.wikipedia.org/wiki/Office_Open_XML) 
(aka OOXML) such as MS Office 2007+ documents, XPS or MSIX files.

For example, oletools can detect, extract and analyse VBA macros, OLE objects, Excel 4 macros (XLM) and DDE links.

See [http://www.decalage.info/python/oletools](http://www.decalage.info/python/oletools) for more info.  

**Quick links:** 
[Home page](http://www.decalage.info/python/oletools) - 
[Download/Install](https://github.com/decalage2/oletools/wiki/Install) -
[Documentation](https://github.com/decalage2/oletools/wiki) -
[Report Issues/Suggestions/Questions](https://github.com/decalage2/oletools/issues) -
[Contact the Author](http://decalage.info/contact) - 
[Repository](https://github.com/decalage2/oletools) -
[Updates on Twitter](https://twitter.com/decalage2)
[Cheatsheet](https://github.com/decalage2/oletools/blob/master/cheatsheet/oletools_cheatsheet.pdf)

Note: python-oletools is not related to OLETools published by BeCubed Software.

News
----

- **2025-05-22 v0.60.3**:
    - olevba: 
      - fixed a security issue in the CLI display when ANSI escape codes are present (PR #873)
      - encrypted files: password is now reported in the logs, added --decrypted_dir option (PR #842)
- **2024-07-02 v0.60.2**:
    - olevba: 
      - fixed a bug in open_slk (issue #797, PR #769)
      - fixed a bug due to new PROJECTCOMPATVERSION record in dir stream (PR #723, issues #700, #701, #725, #791, #808, #811, #833)
    - oleobj: fixed SyntaxError with Python 3.12 (PR #855), SyntaxWarning (PR #774)
    - rtfobj: fixed SyntaxError with Python 3.12 (PR #854)
    - clsid: added CLSIDs for MSI, Zed
    - ftguess: added MSI, PNG and OneNote formats
    - pyxswf: fixed python 3.12 compatibility (PR #841, issue #813)
    - setup/requirements: allow pyparsing 3 to solve install issues (PR #812, issue #762)
- **2022-05-09 v0.60.1**:
    - olevba: 
      - fixed a bug when calling XLMMacroDeobfuscator (PR #737)
      - removed keyword "sample" causing false positives
    - oleid: fixed OleID init issue (issue #695, PR #696)
    - oleobj: 
      - added simple detection of CVE-2021-40444 initial stage
      - added detection for customUI onLoad
      - improved handling of incorrect filenames in OLE package (PR #451)
    - rtfobj: fixed code to find URLs in OLE2Link objects for Py3 (issue #692)
    - ftguess: 
      - added PowerPoint and XPS formats (PR #716)
      - fixed issue with XPS and malformed documents (issue #711)
      - added XLSB format (issue #758)
    - improved logging with common module log_helper (PR #449)
- **2021-06-02 v0.60**:
    - ftguess: new tool to identify file formats and containers (issue #680)
    - oleid: (issue #679)
        - each indicator now has a risk level
        - calls ftguess to identify file formats  
        - calls olevba+mraptor to detect and analyse VBA+XLM macros 
    - olevba:
        - when XLMMacroDeobfuscator is available, use it to extract and deobfuscate XLM macros
    - rtfobj:
        - use ftguess to identify file type of OLE Package (issue #682)
        - fixed bug in re_executable_extensions
    - crypto: added PowerPoint transparent password '/01Hannes Ruescher/01' (issue #627)
    - setup: XLMMacroDeobfuscator, xlrd2 and pyxlsb2 added as optional dependencies 

See the [full changelog](https://github.com/decalage2/oletools/wiki/Changelog) for more information.

Tools:
------

### Tools to analyze malicious documents

- [oleid](https://github.com/decalage2/oletools/wiki/oleid): to analyze OLE files to detect specific characteristics usually found in malicious files.
- [olevba](https://github.com/decalage2/oletools/wiki/olevba): to extract and analyze VBA Macro source code from MS Office documents (OLE and OpenXML).
- [MacroRaptor](https://github.com/decalage2/oletools/wiki/mraptor): to detect malicious VBA Macros
- [msodde](https://github.com/decalage2/oletools/wiki/msodde): to detect and extract DDE/DDEAUTO links from MS Office documents, RTF and CSV
- [pyxswf](https://github.com/decalage2/oletools/wiki/pyxswf): to detect, extract and analyze Flash objects (SWF) that may
  be embedded in files such as MS Office documents (e.g. Word, Excel) and RTF,
  which is especially useful for malware analysis.
- [oleobj](https://github.com/decalage2/oletools/wiki/oleobj): to extract embedded objects from OLE files.
- [rtfobj](https://github.com/decalage2/oletools/wiki/rtfobj): to extract embedded objects from RTF files.

### Tools to analyze the structure of OLE files

- [olebrowse](https://github.com/decalage2/oletools/wiki/olebrowse): A simple GUI to browse OLE files (e.g. MS Word, Excel, Powerpoint documents), to
  view and extract individual data streams.
- [olemeta](https://github.com/decalage2/oletools/wiki/olemeta): to extract all standard properties (metadata) from OLE files.
- [oletimes](https://github.com/decalage2/oletools/wiki/oletimes): to extract creation and modification timestamps of all streams and storages.
- [oledir](https://github.com/decalage2/oletools/wiki/oledir): to display all the directory entries of an OLE file, including free and orphaned entries.
- [olemap](https://github.com/decalage2/oletools/wiki/olemap): to display a map of all the sectors in an OLE file.


Projects using oletools:
------------------------

oletools are used by a number of projects and online malware analysis services,
including
[ACE](https://github.com/IntegralDefense/ACE),
[ADAPT](https://www.blackhat.com/eu-23/briefings/schedule/index.html#unmasking-apts-an-automated-approach-for-real-world-threat-attribution-35162),
[Anlyz.io](https://sandbox.anlyz.io/),
[AssemblyLine](https://www.cse-cst.gc.ca/en/assemblyline),
[Binary Refinery](https://github.com/binref/refinery),
[CAPE](https://github.com/kevoreilly/CAPEv2),
[CinCan](https://cincan.io),
[Cortex XSOAR (Palo Alto)](https://cortex.marketplace.pan.dev/marketplace/details/Oletools/),
[Cuckoo Sandbox](https://github.com/cuckoosandbox/cuckoo),
[DARKSURGEON](https://github.com/cryps1s/DARKSURGEON),
[Deepviz](https://sandbox.deepviz.com/),
[DIARIO](https://diario.elevenpaths.com/),
[dridex.malwareconfig.com](https://dridex.malwareconfig.com),
[EML Analyzer](https://github.com/ninoseki/eml_analyzer),
[EXPMON](https://pub.expmon.com/),
[FAME](https://certsocietegenerale.github.io/fame/),
[FLARE-VM](https://github.com/fireeye/flare-vm),
[GLIMPS Malware](https://www.glimps.fr/en/glimps-malware-2/),
[Hybrid-analysis.com](https://www.hybrid-analysis.com/),
[InQuest Labs](https://labs.inquest.net/),
[IntelOwl](https://github.com/certego/IntelOwl),
[Joe Sandbox](https://www.document-analyzer.net/),
[Laika BOSS](https://github.com/lmco/laikaboss),
[MacroMilter](https://github.com/sbidy/MacroMilter),
[mailcow](https://mailcow.email/),
[malshare.io](https://malshare.io),
[malware-repo](https://github.com/Tigzy/malware-repo),
[Malware Repository Framework (MRF)](https://www.adlice.com/download/mrf/),
[MalwareBazaar](https://bazaar.abuse.ch/),
[olefy](https://github.com/HeinleinSupport/olefy),
[Pandora](https://github.com/pandora-analysis/pandora),
[PeekabooAV](https://github.com/scVENUS/PeekabooAV),
[pcodedmp](https://github.com/bontchev/pcodedmp),
[PyCIRCLean](https://github.com/CIRCL/PyCIRCLean),
[QFlow](https://www.quarkslab.com/products-qflow/),
[Qu1cksc0pe](https://github.com/CYB3RMX/Qu1cksc0pe),
[Tylabs QuickSand](https://github.com/tylabs/quicksand),
[REMnux](https://remnux.org/),
[Snake](https://github.com/countercept/snake),
[SNDBOX](https://app.sndbox.com),
[Splunk add-on for MS O365 Email](https://splunkbase.splunk.com/app/5365/),
[SpuriousEmu](https://github.com/ldbo/SpuriousEmu),
[Strelka](https://github.com/target/strelka),
[stoQ](https://stoq.punchcyber.com/),
[Sublime Platform/MQL](https://docs.sublimesecurity.com/docs/enrichment-functions),
[Subparse](https://github.com/jstrosch/subparse),
[TheHive/Cortex](https://github.com/TheHive-Project/Cortex-Analyzers),
[ThreatBoook](https://s.threatbook.com/),
[TSUGURI Linux](https://tsurugi-linux.org/),
[Vba2Graph](https://github.com/MalwareCantFly/Vba2Graph),
[Viper](http://viper.li/),
[ViperMonkey](https://github.com/decalage2/ViperMonkey),
[YOMI](https://yomi.yoroi.company),
and probably [VirusTotal](https://www.virustotal.com), 
[FileScan.IO](https://www.filescan.io). 
And quite a few [other projects on GitHub](https://github.com/search?q=oletools&type=Repositories).
(Please [contact me]((http://decalage.info/contact)) if you have or know
a project using oletools)


Download and Install:
---------------------

The recommended way to download and install/update the **latest stable release**
of oletools is to use [pip](https://pip.pypa.io/en/stable/installing/):

- On Linux/Mac: `sudo -H pip install -U oletools[full]`
- On Windows: `pip install -U oletools[full]`

This should automatically create command-line scripts to run each tool from
any directory: `olevba`, `mraptor`, `rtfobj`, etc.

The keyword `[full]` means that all optional dependencies will be installed, such as XLMMacroDeobfuscator.
If you prefer a lighter version without optional dependencies, just remove `[full]` from the command line.
 

To get the **latest development version** instead:

- On Linux/Mac: `sudo -H pip install -U https://github.com/decalage2/oletools/archive/master.zip`
- On Windows: `pip install -U https://github.com/decalage2/oletools/archive/master.zip`

See the [documentation](https://github.com/decalage2/oletools/wiki/Install)
for other installation options.

Documentation:
--------------

The latest version of the documentation can be found [online](https://github.com/decalage2/oletools/wiki), otherwise
a copy is provided in the doc subfolder of the package.


How to Suggest Improvements, Report Issues or Contribute:
---------------------------------------------------------

This is a personal open-source project, developed on my spare time. Any contribution, suggestion, feedback or bug 
report is welcome.

To suggest improvements, report a bug or any issue, please use the 
[issue reporting page](https://github.com/decalage2/oletools/issues), providing all the
information and files to reproduce the problem. 

You may also [contact the author](http://decalage.info/contact) directly to provide feedback.

The code is available in [a GitHub repository](https://github.com/decalage2/oletools). You may use it
to submit enhancements using forks and pull requests.

License
-------

This license applies to the python-oletools package, apart from the thirdparty folder which contains third-party files 
published with their own license.

The python-oletools package is copyright (c) 2012-2024 Philippe Lagadec (http://www.decalage.info)

All rights reserved.

Redistribution and use in source and binary forms, with or without modification,
are permitted provided that the following conditions are met:

 * Redistributions of source code must retain the above copyright notice, this
   list of conditions and the following disclaimer.
 * Redistributions in binary form must reproduce the above copyright notice,
   this list of conditions and the following disclaimer in the documentation
   and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.


----------

olevba contains modified source code from the officeparser project, published
under the following MIT License (MIT):

officeparser is copyright (c) 2014 John William Davison

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
