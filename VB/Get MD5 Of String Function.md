### Calculate the MD5 hash of a string:


```vb
 
#Region " Get MD5 Of String Function "
 
    ' [ Get MD5 Of String Function ]
    '
    ' Examples :
    '
    ' MsgBox(Get_MD5_Of_String("C:\Test.txt"))
 
    Private Function Get_MD5_Of_String(ByVal str As String) As String
        Dim MD5_Hex As String = Nothing
        Dim MD5 As New System.Security.Cryptography.MD5CryptoServiceProvider()
        Dim MD5_Byte = System.Text.Encoding.UTF8.GetBytes(str)
        Dim MD5_Hash = MD5.ComputeHash(MD5_Byte)
        MD5.Clear()
        For Number As Integer = 0 To MD5_Hash.Length - 1 : MD5_Hex &= MD5_Hash(Number).ToString("x").PadLeft(2, "0") : Next
        Return MD5_Hex
    End Function
 
#End Region

``` 