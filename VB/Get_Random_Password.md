### Get Random Password


```vb
 
   ' USAGE:
    '
    ' MsgBox(Get_Random_Password(8))
    ' MsgBox(Get_Random_Password(36))
 
#Region " Get Random Password Function "
 
    Public Function Get_Random_Password(ByVal Password_Length As Double) As String
        Dim New_Password As String = System.Guid.NewGuid.ToString
        If Password_Length <= 0 OrElse Password_Length > New_Password.Length Then
            Throw New ArgumentException("Length must be between 1 and " & New_Password.Length)
        End If
        Return New_Password.Substring(0, Password_Length)
    End Function
 
#End Region

``` 