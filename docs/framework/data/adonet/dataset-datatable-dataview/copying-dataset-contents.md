---
title: Kopieren von DataSet-Inhalten
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: cb846617-2b1a-44ff-bd7f-5835f5ea37fa
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 69709fea628e6cb1d10a23f29b60911ab07e1111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2017
---
# <a name="copying-dataset-contents"></a>Kopieren von DataSet-Inhalten
Sie können eine Kopie erstellen eine <xref:System.Data.DataSet> , damit Sie mit Daten arbeiten, ohne Auswirkungen auf die ursprünglichen Daten oder arbeiten können mit einer Teilmenge der Daten aus einer **DataSet**. Beim Kopieren einer **DataSet**, können Sie:  
  
-   Erstellt eine genaue Kopie der **DataSet**, einschließlich Schema, Daten, Informationen zum Zeilenstatus und Zeilenversionen.  
  
-   Erstellen einer **DataSet** , enthält das Schema einer vorhandenen **DataSet**, aber nur Zeilen, die geändert wurden. Sie können alle Zeilen zurückgeben, die geändert wurden, oder geben Sie einen bestimmten **DataRowState**. Weitere Informationen zum Zeilenstatus finden Sie unter [Zeilenstatus und Zeilenversionen](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md).  
  
-   Kopieren Sie das Schema oder die relationale Struktur von den **DataSet** nur, ohne alle Zeilen kopiert. Zeilen können mit <xref:System.Data.DataTable> in eine vorhandene <xref:System.Data.DataTable.ImportRow%2A> importiert werden.  
  
 So erstellen eine genaue Kopie der **DataSet** , Schema und Daten enthält, verwenden Sie die <xref:System.Data.DataSet.Copy%2A> Methode der **DataSet**. Im folgenden Codebeispiel wird veranschaulicht, wie eine genaue Kopie erstellen die **DataSet**.  
  
```vb  
Dim copyDataSet As DataSet = customerDataSet.Copy()  
```  
  
```csharp  
DataSet copyDataSet = customerDataSet.Copy();  
```  
  
 So erstellen eine Kopie einer **DataSet** , die enthält das Schema und nur die Daten darstellt **Added**, **"geändert"**, oder **gelöschte** Zeilen verwenden die <xref:System.Data.DataSet.GetChanges%2A> Methode der **DataSet**. Können Sie auch **GetChanges** zurückzugebenden nur Zeilen mit dem angegebenen Zeilenstatus durch Übergeben einer **DataRowState** Wert, der beim Aufrufen von **GetChanges**. Das folgende Codebeispiel veranschaulicht das Übergeben einer **DataRowState** beim Aufrufen von **GetChanges**.  
  
```vb  
' Copy all changes.  
Dim changeDataSet As DataSet = customerDataSet.GetChanges()  
' Copy only new rows.  
Dim addedDataSetAs DataSet = _  
    customerDataSet.GetChanges(DataRowState.Added)  
```  
  
```csharp  
// Copy all changes.  
DataSet changeDataSet = customerDataSet.GetChanges();  
// Copy only new rows.  
DataSet addedDataSet= customerDataSet.GetChanges(DataRowState.Added);  
```  
  
 So erstellen eine Kopie einer **DataSet** , die nur Schema enthält, verwenden Sie die <xref:System.Data.DataSet.Clone%2A> Methode der **DataSet**. Sie können auch vorhandene Zeilen hinzufügen, um das geklonte **DataSet** mithilfe der **ImportRow** Methode der **DataTable**. **ImportRow** der angegebenen Tabelle Daten, Zeilenstatus und Versionsinformationen für die Zeile hinzugefügt. Spaltenwerte werden nur hinzugefügt, wenn der Spaltenname übereinstimmt und der Datentyp kompatibel ist.  
  
 Das folgende Codebeispiel erstellt einen Klon des eine **DataSet** und fügt dann die Zeilen aus der ursprünglichen **DataSet** auf die **Kunden** -Tabelle in der **DataSet**  -Klon für Kunden, wo die **CountryRegion** Spalte hat den Wert "Germany".  
  
```vb  
Dim customerDataSet As New DataSet  
        customerDataSet.Tables.Add(New DataTable("Customers"))  
        customerDataSet.Tables("Customers").Columns.Add("Name", GetType(String))  
        customerDataSet.Tables("Customers").Columns.Add("CountryRegion", GetType(String))  
        customerDataSet.Tables("Customers").Rows.Add("Juan", "Spain")  
        customerDataSet.Tables("Customers").Rows.Add("Johann", "Germany")  
        customerDataSet.Tables("Customers").Rows.Add("John", "UK")  
  
Dim germanyCustomers As DataSet = customerDataSet.Clone()  
  
Dim copyRows() As DataRow = _  
  customerDataSet.Tables("Customers").Select("CountryRegion = 'Germany'")  
  
Dim customerTable As DataTable = germanyCustomers.Tables("Customers")  
Dim copyRow As DataRow  
  
For Each copyRow In copyRows  
  customerTable.ImportRow(copyRow)  
Next  
```  
  
```csharp  
DataSet customerDataSet = new DataSet();  
customerDataSet.Tables.Add(new DataTable("Customers"));  
customerDataSet.Tables["Customers"].Columns.Add("Name", typeof(string));  
customerDataSet.Tables["Customers"].Columns.Add("CountryRegion", typeof(string));  
customerDataSet.Tables["Customers"].Rows.Add("Juan", "Spain");  
customerDataSet.Tables["Customers"].Rows.Add("Johann", "Germany");  
customerDataSet.Tables["Customers"].Rows.Add("John", "UK");  
  
DataSet germanyCustomers = customerDataSet.Clone();  
  
DataRow[] copyRows =   
  customerDataSet.Tables["Customers"].Select("CountryRegion = 'Germany'");  
  
DataTable customerTable = germanyCustomers.Tables["Customers"];  
  
foreach (DataRow copyRow in copyRows)  
  customerTable.ImportRow(copyRow);  
```  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Data.DataSet>  
 <xref:System.Data.DataTable>  
 [DataSets, DataTables und DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Managed Provider und DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)
