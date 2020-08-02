### Calculate the MD5 hash of a file:


```vb
 
   #Region " Get MD5 Of File Function "
 
       ' [ Get MD5 Of File Function ]
       '
       ' Examples :
       '
       ' MsgBox(Get_MD5_Of_File("C:\Test.txt"))
 
       Private Function Get_MD5_Of_File(ByVal File As String) As String
           Using MD5_Reader As New System.IO.FileStream(File, IO.FileMode.Open, IO.FileAccess.Read)
               Using MD5 As New System.Security.Cryptography.MD5CryptoServiceProvider
                   Dim MD5_Byte() As Byte = MD5.ComputeHash(MD5_Reader)
                   Dim MD5_Hex As New System.Text.StringBuilder(MD5.ComputeHash(MD5_Reader).Length * 2)
                   For Number As Integer = 0 To MD5_Byte.Length - 1 : MD5_Hex.Append(MD5_Byte(Number).ToString("X2")) : Next
                   Return MD5_Hex.ToString().ToLower
               End Using
           End Using
       End Function
 
    #End Region

``` 