var sheetID = '1ofolHs9okA_OD1RgXchBZq168BxAUox-Qn7dwXBF7JI';

var tc = 5; //your target column to dedupe on

var ss = SpreadsheetApp.openById(sheetID);

var s1 = SpreadsheetApp.getActiveSheet();

function getUniqueRowNumbers(matchArr){
  var unqArr = [];
  matchArr.filter(function(elm,pos,arr){    
    if(arr.indexOf(elm) == pos){
      unqArr.push(arr.indexOf(elm));
    }  
  });
  return unqArr;
}

function deDoop(){
  var colToClean = [].concat.apply([], s1.getRange(1,tc,s1.getLastRow(),1).getValues());
  var rowsToPull = getUniqueRowNumbers(colToClean);

  var dd = ss.insertSheet("deDuped_"+s1.getSheetName());
  var allRows = s1.getRange(1,1,s1.getLastRow(), s1.getLastColumn()).getValues();
  var newSheetCols = [];
  for(i=0; i<rowsToPull.length; i++){
    var r = rowsToPull[i];
    newSheetCols.push(allRows[r]);
  }
  dd.getRange(1,1,newSheetCols.length,newSheetCols[0].length).setValues(newSheetCols);
}

