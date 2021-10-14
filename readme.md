## Introduction
"Data management plan generator" can create a data management plan automatically. 
This tool is purely web-based, front end and written in javascript. 
Currently both the input and output are .odt files. 

To try this tool, you can go to [this link](http://xrzhou.com/generator) or [another link](https://nfdi4plants.github.io/plan-generator/)

An example output is generated and stored as "output.odt" in the root folder.
The "What you see is what you get" editor is from WEBODF developed by a Germany company KO GmbH https://webodf.org/. After trying many online docx editor or generator, I found using javascript to modify the webodf is the best way.

Tools I had a look at:

1. docx.js https://docx.js.org a good library, but no GUI web editor. As we already had a document, we don't need to generate a document from ground up.
2. docxtemplater https://github.com/open-xml-templating/docxtemplater the most similar project. It has both open source and commercial version. Well designed template and good maintenance. However, a. they use a different type of place holder; b. Their input is json, which means that another json generation layer need to be used; c. no "What you see is what you get" editor. 
3. docx4j https://www.docx4java.org/trac/docx4j use java backend. For handling a small document, it seems a overkill, it has no "What you see is what you get" editor.
4. redocx https://github.com/nitin42/redocx did not try it, but seem similar to docx.js and with a react interface. It runs only on backends and no GUI
5. onlyoffice https://www.onlyoffice.com/ could be a good combination with docx.js. But it has at least 1500 $ fee to use and seems quite heavy lifting. Could be give a try if current solution is too hard.


###libraries:
Bootstrap
WEBODF
FileSaver.js


### Current functions:
Generally all functions works. There are still some bugs but no hard barriers. Works smoother than I expected.
Although some questions and keywords are mismatched, see next sections.

1. replace any $_KEYWORDS in the text. It avoids replacing $_KEYWORDSEXTENDED or $_KEYWORDS1|KEYWORDS2 or #if_$KEYWORDS. This is wraped in find_replace function.
2. By using check boxes, it removes #if_ and #endif_ around the $_KEYWORDS in the checked boxes and removes all text in the unchecked keywords. Then replace the selected keywords. It can also handle | symbol. The "!" is not implemented. 
3. Automatic expose hidden sub-question in question 5., if user does not use DataPLANT, then she/he need to answer question 5a.
  


### Known issues:
1. Bug (fixed) in question 2, where the user need to click the white space near the checkbox before submit a input. Might be caused by changing focus of the "window.find()"  function. Tried several debug possibilities, one way to debug this one is to refresh the object, but brings bug 3.(:P), others are not working. 
2. Bug of undo button. Clicking the undo button will cause document not manually editable. However the automatic modification is not affected.
3. Compatibility is only tested in chrome. In theory IE support is not hard to add.


### Missing or mismatched questions and keywords.
Missing:
1. $_PROTECT RENAME project name to general project information and add it there 
2. $_UPDATE RENAME project name to general project information and add it there 
3. $_VISUALIZATION Add section Data Analysis
4. $_STUDYOBJECT  RENAME project name to general project information and add it there 
5. $_PREVIOUSPROJECTS RENAME project name to general project information and add it there 
6. $_INDUSTRY  RENAME project name to general project information and add it there 
7. $_PROPRIETARY RENAME project name to general project information and add it there 
8. \#issuewarning 
9. $_DATAOFFICER RENAME project name to general project information and add it there 

RENAME project name to general project information and merge 5. use data plant in there
RENAME project name to general project information and merge 7. EU in there
MERGE 4 relevant standard and 6 other standardsv and use 6 as a subsection in there first

