---
title: Appscript
date: 2024-02-01
---

google's javascript interface for scrpiting features into gapps

here's an example script I acutally use to get url links from richtext cells
```javascript
function GetURL(input) {
  var myFormula = SpreadsheetApp.getActiveRange().getFormula();
  var myAddress = myFormula.replace(/=.*?\(/,'').replace(')','');
  var myRange = SpreadsheetApp.getActiveSheet().getRange(myAddress);
  var richTextValues = myRange.getRichTextValue().getRuns();
  var urls = [];
  for (var i = 0 ; i < richTextValues.length; i++) {
    var url = richTextValues[i].getLinkUrl();
    if (url) {
      urls.push(url);
    }
  }
  return [urls];
};
```
