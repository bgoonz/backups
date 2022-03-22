# md and html | webdevhub

[https://bgoonz-blog.netlify.app/docs/tools/markdown-html/](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/)

# Paste To Markdown

# Paste to Markdown

## Instructions

1. Find the text to convert to Markdown (*e.g.*, in another browser tab)
2. Copy it to the clipboard (`Ctrl+C`, or `⌘+C` on Mac)
3. Paste it into this window (`Ctrl+V`, or `⌘+V` on Mac)
4. The converted Markdown will appear!

The conversion is carried out by [to-markdown](https://github.com/domchristie/to-markdown), a Markdown converter written in JavaScript and running locally in the browser.

# Paste Excel Tabel To Markdown

# Copy Excel Paste Markdown

# Paste excel to HTML

# USAGE

## cd src --> node index.js name-of-excel-file.xlsx

# DEMO!

## This repository contains code made to read a microsoft excel file contained within it's outer folder structure and convert it into a html table.

## 

![https://bgoonz-blog.netlify.app/docs/tools/markdown-html/assets/2021-01-27-14-27-34.png](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/assets/2021-01-27-14-27-34.png)

## > As you can see from the difference between the screenshot of the source spreadsheet and it's html rendering …. this project is still a work in progress.

## 

![https://bgoonz-blog.netlify.app/docs/tools/markdown-html/assets/screencapture-127-0-0-1-5500-testing-SampleData-html-2021-01-27-14_42_01.png](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/assets/screencapture-127-0-0-1-5500-testing-SampleData-html-2021-01-27-14_42_01.png)

## WITHOUT TARGETED STYLING BELOW:

[Untitled](md%20and%20htm%20ef718/Untitled%20D%20d555b.csv)

```
\___________________________________________________
bryan_dir:excel-2-html-table_exitstatus:0 ====>
tree -d -L 2
.
├── assets
├── doccumentation
└── src
    └── node_modules
4 directories
\___________________________________________________
bryan_dir:excel-2-html-table_exitstatus:0 ====>
tree -L 2
.
├── README.md
├── SampleData.html
├── SampleData.xlsx
├── assets
│   ├── 2021-01-27-14-27-34.png
│   └── 2021-01-27-14-31-00.png
├── doccumentation
│   ├── cheerio.md
│   ├── notes.md
│   └── xlsx.md
├── src
│   ├── index.js
│   ├── node_modules
│   ├── package-lock.json
│   └── package.json
└── ~$SampleData.xlsx
4 directories, 12 files

```

```
"use strict";
let fs = require('fs');
let process = require('process');
let workingDirectory = process.cwd().slice(2);
let XLSX = require('xlsx');
let workbook = XLSX.readFile(process.argv[2]);
let sheets = workbook.Sheets;
let htmlFile = '';
let rowNumber;
let htmlArray;
// Check to make sure user provides argument for command line
if (typeof process.argv[2] === 'undefined') {
 console.log('\n' + 'Error:' + '\n' + 'You must enter the excel file you wish to build tables from as an argument' + '\n' + 'i.e., node toTable.js resolutions.xlsx');
 return;
} else {
 // Check that the file is the correct type
 if (process.argv[2].slice(-4) !== 'xlsx') {
 console.log('\n' + 'This program will only convert xlsx files' + '\n' + 'Please enter correct file type');
 return;
 } else {
 // Create the HTML file name to write the table to
 var fileName = process.argv[2];
 var newFileName = fileName.slice(0, -4) + 'html';
 }
}
//htmlFile += '<html>' + '\n' + '<body>' +'\n';
function getPosition(string, subString, index) {
 return string.split(subString, index).join(subString).length;
}
// Iterate through each worksheet in the workbook
for (var sheet in sheets) {
 // Start building a new table if the worksheet has entries
 if (typeof sheet !== 'undefined') {
 htmlFile += '<table summary="" class="turntable">' + '\n' + '<thead>';
 // Iterate over each cell value on the sheet
 for (var cell in sheets[sheet]) {
 // Protect against undefined values
 if (typeof sheets[sheet][cell].w !== 'undefined') {
 //The first row in the table
 if (cell === 'A1') {
 htmlFile += '\n' + '<tr>' + '\n' + '<th>' + sheets[sheet][cell].w.replace('& ', '&amp;').replace('-', '&ndash;').replace('–', '&mdash;') + '</th>';
 } else {
 //The second row in the table closes the thead element
 if (cell === 'A2') {
 htmlFile += '\n' + '</tr>' + '\n' + '</thead>' + '\n' + '<tr>' + '\n' + '<th>' + sheets[sheet][cell].w.replace('& ', '&amp;').replace('-', '&ndash;').replace('–', '&mdash;') + '</th>';
 } else {
 // The first cell in each row
 if (cell.slice(0, 1) === 'A') {
 htmlFile += '\n' + '</tr>' + '\n' + '<tr>' + '\n' + '<th>' + sheets[sheet][cell].w.replace('& ', '&amp;').replace('-', '&ndash;').replace('–', '&mdash;') + '</th>';
 //All the other cells
 } else {
 htmlFile += '\n' + '<td>' + sheets[sheet][cell].w.replace('& ', '&amp;').replace('-', '&ndash;').replace('–', '&mdash') + '</td>';
 }
 }
 }
 }
 }
 // Close the table
 htmlFile += '\n' + '</tr>' + '\n' + '</table>' + '\n';
 }
 /*console.log(sheets[sheet]['!merges']);
 sheets[sheet]['!merges'].forEach(function(merge, index) {
 //console.log(merge);
 rowNumber = (getPosition(htmlFile, '<th>', (merge.s.r+1)) + 3);
 console.log(rowNumber);
 htmlArray = htmlFile.split('');
 htmlArray.splice(rowNumber, 0, ' colspan="3"');
 htmlFile = htmlArray.join('');
 });*/
}
// Close the file
//htmlFile += '</body>' + '\n' + '</html>';
// Write htmlFile variable to the disk with newFileName as the name
fs.writeFile(newFileName, htmlFile, (err) => {
 if (err) throw err;
 console.log('\n' +'Your tables have been created in', newFileName);
});
```

- [./DEMO](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/Demo.html)
- [./doccumentation/cheerio.html](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/doccumentation/cheerio.html)
- [./doccumentation/notes.html](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/doccumentation/notes.html)
- [./doccumentation/process-argv.html](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/doccumentation/process-argv.html)
- [./doccumentation/xlsx.html](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/doccumentation/xlsx.html)
- [./index.html](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/index.html)
- [./testing/SampleData.html](https://bgoonz-blog.netlify.app/docs/tools/markdown-html/testing/SampleData.html)
