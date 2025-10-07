function appendNewHighRiskRows() {
  var ss = SpreadsheetApp.getActiveSpreadsheet();
  var sourceSheet = ss.getSheetByName('Sheet1');
  var destSheet = ss.getSheetByName('HighRiskPatient');

  var props = PropertiesService.getDocumentProperties();
  var lastRowSource = sourceSheet.getLastRow();
  var lastCol = sourceSheet.getLastColumn();

  // loop every row from row 2 downwards
  for (var rowNum = 2; rowNum <= lastRowSource; rowNum++) {
    var processedKey = 'row_' + rowNum;
    if (props.getProperty(processedKey)) continue; // already processed

    var rowValues = sourceSheet.getRange(rowNum, 1, 1, lastCol).getValues()[0];
    var colH = rowValues[7]; // H column index 7
    if (colH && colH.toString().toLowerCase().indexOf('high risk') !== -1) {
      destSheet.appendRow(rowValues);
    }

    // mark this source row as processed regardless of High Risk
    props.setProperty(processedKey, '1');
  }
}
