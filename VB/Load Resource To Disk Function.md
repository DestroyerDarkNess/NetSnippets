### Upload an embedded resource (.exe) to the hard disk


```vb
 
#Region " Load Resource To Disk Function "
 
    ' [ Load Exe Resource To Disk Function ]
    '
    ' // By Elektro H@cker (Gracias a Kubox)
    '
    ' Examples:
    '
    ' Load__Exe_Resource_To_Disk(My.Resources.Exe_Name, "C:\File.exe")
    ' ' Process.Start("C:\File.exe")
 
    Private Function Load__Exe_Resource_To_Disk(ByVal Resource As Byte(), ByVal Target_File As String) As Boolean
        Try
            Dim File_Buffer As Byte() = Resource
            Dim Buffer_FileStream As New IO.FileStream(Target_File, IO.FileMode.Create, IO.FileAccess.Write)
            Buffer_FileStream.Write(File_Buffer, 0, File_Buffer.Length) : Buffer_FileStream.Close()
            Return True
        Catch ex As Exception
            Return False
        End Try
    End Function
 
#End Region

``` 