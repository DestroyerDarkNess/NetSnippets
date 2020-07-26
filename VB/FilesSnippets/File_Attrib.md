 -Modify file attributes:

```vb
   ' Usage:
    ' Attrib("File.txt", IO.FileAttributes.ReadOnly + IO.FileAttributes.Hidden)
    ' If Attrib("File.txt", IO.FileAttributes.System) Is Nothing Then MsgBox("File doesn't exist!")
 
      Private Function Attrib(ByVal File As String, ByVal Attributes As System.IO.FileAttributes)
        If IO.File.Exists(File) Then
            Try
                FileSystem.SetAttr(File, Attributes)
                Return True ' File was modified OK
            Catch ex As Exception
                ' MsgBox(ex.Message)
                Return False ' File can't be modified maybe because User Permissions
            End Try
        Else
            Return Nothing ' File doesn't exist
        End If
    End Function
```