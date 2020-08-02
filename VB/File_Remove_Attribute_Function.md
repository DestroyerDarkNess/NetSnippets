### Function to remove attributes from a file, preserving the rest of attributes.


```vb
 
#Region " File Remove Attribute Function "
 
    ' [ File Remove Attribute Function ]
    '
    ' Examples :
    '
    ' MsgBox(File_Remove_Attribute("C:\Test.txt", FileAttribute.ReadOnly))
    ' MsgBox(File_Remove_Attribute("C:\Test.txt", FileAttribute.ReadOnly + FileAttribute.Hidden))
 
    Public Function File_Remove_Attribute(ByVal File As String, ByVal Remove_Attribute As FileAttribute) As Boolean
        Try
            Dim FileAttributes As FileAttribute = IO.File.GetAttributes(File)
            IO.File.SetAttributes(File, FileAttributes And Not Remove_Attribute)
            Return True
        Catch ex As Exception
            Return False
        End Try
    End Function
 
#End Region

``` 