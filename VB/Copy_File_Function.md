### Copy File, to copy files, with the option to create the directory if it does not exist, the option to replace files, and the option to apply attributes to the file.


```vb
 
#Region " Copy File Function "
 
    ' [ Copy File Function ]
    '
    ' // By Elektro H@cker
    '
    ' Examples :
    '
    ' MsgBox(Copy_File("C:\File.txt", "C:\Test\")) ' Standard copy
    ' MsgBox(Copy_File("C:\File.txt", "C:\Test\", True)) ' Create the directory if doesn't exists
    ' MsgBox(Copy_File("C:\File.txt", "C:\Test\", , True)) ' Replace any existing file
    ' MsgBox(Copy_File("C:\File.txt", "C:\Test\", , , IO.FileAttributes.Hidden + IO.FileAttributes.ReadOnly)) ' Apply new attributes
 
    Private Function Copy_File(ByVal File As String, ByVal Target_Path As String, _
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
            My.Computer.FileSystem.CopyFile(File, Target_Path & "\" & File_Information.Name, Force_File_Replace) ' Copies the file
            If Not Attributes = IO.FileAttributes.Normal Then My.Computer.FileSystem.GetFileInfo(Target_Path & "\" & File_Information.Name).Attributes = Attributes ' Apply File Attributes
            Return True ' File is copied OK
        Catch ex As Exception
            'Return False
            Return ex.Message ' File can't be created maybe beacuse user permissions
        End Try
    End Function
 
#End Region

``` 