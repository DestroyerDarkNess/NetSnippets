### Get Printers


```vb
 
   ' // By Elektro H@cker
    ' 
    ' USAGE:
    '
    '  For Each Printer_Name In Get_Printers() : MsgBox(Printer_Name) : Next
 
    Private Function Get_Printers()
        Dim Printer_Array As New List(Of String)
        Try
            For Each Printer_Name As String In System.Drawing.Printing.PrinterSettings.InstalledPrinters : Printer_Array.Add(Printer_Name) : Next
        Catch ex As Exception
            If ex.Message.Contains("RPC") Then Return "RPC Service is not avaliable"
        End Try
        Return Printer_Array
    End Function

``` 