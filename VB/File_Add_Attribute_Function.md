### Function to add attributes to a file, preserving the rest of the attributes.


```vb
 
#Region " File Add Attribute Function "
 
    ' [ File Add Attribute Function ]
    '
    ' Examples :
    '
    ' MsgBox(File_Add_Attribute("C:\Test.txt", FileAttribute.ReadOnly))
    ' MsgBox(File_Add_Attribute("C:\Test.txt", FileAttribute.ReadOnly + FileAttribute.Hidden))
 
    Public Function File_Add_Attribute(ByVal File As String, ByVal Add_Attribute As FileAttribute) As Boolean
        Try
            Dim FileAttributes As FileAttribute = IO.File.GetAttributes(File)
            IO.File.SetAttributes(File, FileAttributes Or Add_Attribute)
            Return True
        Catch ex As Exception
            Return False
        End Try
    End Function
 
#End Region

``` 