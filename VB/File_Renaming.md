 -I have made this snippet to speed up the renaming of files, here you have;)

* I use "MOVE" because otherwise it is impossible to rename the file with the same name, as it is well explained here by NovLucker:
http://foro.elhacker.net/net/soluctado_iquestcomo_renombrar_un_archivo_o_carpeta_con_el_mismo_nombre-t378839.0.html

```vb
  ' Usage:
    '
    ' RenameFile("C:\Test.txt", "TeSt.TxT")
    ' RenameFile("C:\Test.txt", "Test", "doc")
    ' RenameFile(FileInfoObject.FullName, FileInfoObject.Name.ToLower, FileInfoObject.Extension.ToUpper)
    ' If RenameFile("C:\Test.txt", "TeSt.TxT") Is Nothing Then MsgBox("El archivo no existe!")
 
#Region " RenameFile function "
 
    Private Function RenameFile(ByVal File As String, ByVal NewFileName As String, Optional ByVal NewFileExtension As String = Nothing)
        If IO.File.Exists(File) Then
            Try
                Dim FileToBeRenamed As New System.IO.FileInfo(File)
                If NewFileExtension Is Nothing Then
                    FileToBeRenamed.MoveTo(FileToBeRenamed.Directory.FullName & "\" & NewFileName) ' Rename file with same extension
                Else
                    FileToBeRenamed.MoveTo(FileToBeRenamed.Directory.FullName & "\" & NewFileName & NewFileExtension) ' Rename file with new extension
                End If
                Return True ' File was renamed OK
            Catch ex As Exception
                ' MsgBox(ex.Message)
                Return False ' File can't be renamed maybe because User Permissions
            End Try
        Else
            Return Nothing ' File doesn't exist
        End If
    End Function
 
#End Region
``` 

 