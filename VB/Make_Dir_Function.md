### Make Dir, to create directories with the option to add attributes.


```vb
 
#Region " Make Dir Function "
 
    ' [ Make Dir Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples :
    '
    ' MsgBox(MakeDir("C:\Test"))
 
    Private Function Make_Dir(ByVal Path As String, Optional ByVal Attributes As System.IO.FileAttributes = IO.FileAttributes.Normal)
        If My.Computer.FileSystem.DirectoryExists(Path) Then Return Nothing ' Directory already exists
        Try
            My.Computer.FileSystem.CreateDirectory(Path) ' Create directory
            If Not Attributes = IO.FileAttributes.Normal Then My.Computer.FileSystem.GetDirectoryInfo(Path).Attributes = Attributes ' Apply Folder Attributes
            Return True ' Directory is created OK
        Catch ex As Exception
            Return False ' Can't create the directory maybe because user permissions
            ' Return ex.Message
        End Try
    End Function
 
#End Region

``` 