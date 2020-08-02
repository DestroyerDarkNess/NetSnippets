### Function that checks if a file has an attribute


```vb
 
#Region " File Have Attribute Function "
 
    ' [ File Have Attribute Function ]
    '
    ' Examples :
    '
    ' MsgBox(File_Have_Attribute("C:\Test.txt", FileAttribute.ReadOnly))
    ' MsgBox(File_Have_Attribute("C:\Test.txt", FileAttribute.ReadOnly + FileAttribute.Hidden))
 
    Public Function File_Have_Attribute(ByVal File As String, ByVal CheckAttribute As FileAttribute) As Boolean
        Try
            Dim FileAttributes As FileAttribute = IO.File.GetAttributes(File)
            If (FileAttributes And CheckAttribute) = CheckAttribute Then Return True Else Return False
        Catch ex As Exception
            Return Nothing
        End Try
 
    End Function
 
#End Region

``` 