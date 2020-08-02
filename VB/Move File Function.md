### Move a file, with several additional options.


```vb
 #Region " Move File Function "
 
    ' [ Move File Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples :
    '
    ' MsgBox(Move_File("C:\File.txt", "C:\Test\")) ' Standard move
    ' MsgBox(Move_File("C:\File.txt", "C:\Test\", True)) ' Create the directory if doesn't exists
    ' MsgBox(Move_File("C:\File.txt", "C:\Test\", , True)) ' Replace any existing file
    ' MsgBox(Move_File("C:\File.txt", "C:\Test\", , , IO.FileAttributes.Hidden + IO.FileAttributes.ReadOnly)) ' Apply new attributes
 
    Private Function Move_File(ByVal File As String, ByVal Target_Path As String, _
                               Optional ByVal Force_Target_Path As Boolean = False, Optional ByVal Force_File_Replace As Boolean = False, _
                               Optional ByVal Attributes As System.IO.FileAttributes = IO.FileAttributes.Normal)
 
        Dim File_Information = My.Computer.FileSystem.GetFileInfo(File) ' Get Input File Information
 
        ' Directory
        If Not Force_Target_Path And Not My.Computer.FileSystem.DirectoryExists(Target_Path) Then
            Return False ' Target Directory don't exists
        ElseIf Force_Target_Path Then
            Try
                My.Computer.FileSystem.CreateDirectory(Target_Path) ' Create directory
            Catch ex As Exception
                'Return False
                Return ex.Message ' Directory can't be created maybe beacuse user permissions
            End Try
        End If
 
        ' File
        Try
            My.Computer.FileSystem.MoveFile(File, Target_Path & "\" & File_Information.Name, Force_File_Replace) ' Moves the file
            If Not Attributes = IO.FileAttributes.Normal Then My.Computer.FileSystem.GetFileInfo(Target_Path & "\" & File_Information.Name).Attributes = Attributes ' Apply File Attributes
            Return True ' File is copied OK
        Catch ex As Exception
            'Return False
            Return ex.Message ' File can't be created maybe beacuse user permissions
        End Try
    End Function
 
#End Region

``` 