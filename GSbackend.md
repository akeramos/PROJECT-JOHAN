const SPREADSHEET_ID = '1VFnL4t4tYZghahOd-ymqiWaFBQmHti0HVcjeze4S4MY';

function doPost(e) {
  try {
    const sheet = SpreadsheetApp.openById(SPREADSHEET_ID).getSheetByName("Sheet1");
    const data = JSON.parse(e.postData.contents);

    sheet.appendRow([
      new Date(),
      data.name || '',
      data.nric || '',
      data.age || '',
      data.gender || '',
      data.status || '',
      data.puma_score || '',
      data.high_risk_note || '',
      data.assess_asthma || '',
      data.assess_copd || '',
      data.assess_lc || '',
      data.assess_tb || '',  
      data.smoke_status || '',
      data.pack_year || '',
      data.phone || '',
      data.suggestion || '',
      data.Ordered || '',
      data.workingDiagnosis || ''
    ]);

    return ContentService.createTextOutput("Success").setMimeType(ContentService.MimeType.TEXT);
  } catch (err) {
    return ContentService.createTextOutput("Error: " + err.message)
      .setMimeType(ContentService.MimeType.TEXT);
  }
}

function doGet() {
  return HtmlService.createHtmlOutput("Endpoint running");
}
