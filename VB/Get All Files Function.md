### The Get All Files snippet, improved:


```vb
 
#Region " Get All Files Function "
 
    ' [ Get All Files Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples:
    '
    ' Dim Files As Array = Get_All_Files("C:\Test", True)
    ' For Each File In Get_All_Files("C:\Test", False) : MsgBox(File) : Next
 
    Private Function Get_All_Files(ByVal Directory As String, Optional ByVal Recursive As Boolean = False) As Array
        If System.IO.Directory.Exists(Directory) Then
            If Not Recursive Then : Return System.IO.Directory.GetFiles(Directory, "*", IO.SearchOption.TopDirectoryOnly)
            Else : Return IO.Directory.GetFiles(Directory, "*", IO.SearchOption.AllDirectories)
            End If
        Else
            Return Nothing
        End If
    End Function
 
#End Region

``` 